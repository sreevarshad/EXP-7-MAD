
# Ex.No:7 Develop an android application to display the place name with image using list view in android studio


### AIM:

To create and develop the application to display the place name with image using list view in android studio

### EQUIPMENTS REQUIRED:

Android Studio(Latest Version).

### ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “listview″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

### PROGRAM:

Program to print the list of item

Developed by:Sreevarsha.D

Registeration Number : 212221040159

activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/list"
        android:layout_width="409dp"
        android:layout_height="729dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

mylist.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ImageView
        android:id="@+id/icon"
        android:layout_width="60dp"
        android:layout_height="60dp"
        android:padding="5dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.076"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.053" />

    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.382"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.063">

        <TextView
            android:id="@+id/title"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="10dp"
            android:layout_marginTop="5dp"
            android:padding="2dp"
            android:text="Medium Text"
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:textColor="#4d4d4d"
            android:textStyle="bold" />

    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```

MyListAdapter.java

```
package com.example.listview;

import android.app.Activity;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ArrayAdapter;
import android.widget.ImageView;
import android.widget.TextView;

public class MyListAdapter extends ArrayAdapter<String> {

    private final Activity context;
    private final String[] maintitle;
    private final Integer[] imgid;

    public MyListAdapter(Activity context, String[] maintitle, Integer[] imgid) {
        super(context, R.layout.mylist, maintitle);
        // TODO Auto-generated constructor stub
        this.context=context;
        this.maintitle=maintitle;
        this.imgid=imgid;
    }
    public View getView(int position, View view, ViewGroup parent) {
        LayoutInflater inflater=context.getLayoutInflater();
        View rowView=inflater.inflate(R.layout.mylist, null,true);

        TextView titleText = (TextView) rowView.findViewById(R.id.title);
        ImageView imageView = (ImageView) rowView.findViewById(R.id.icon);

        titleText.setText(maintitle[position]);
        imageView.setImageResource(imgid[position]);
        return rowView;
    };
}

```
MainActivity.java

```
package com.example.listview;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ListAdapter;
import android.widget.ListView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    ListView list;
    String[] maintitle ={
            "AMERICA","AUSTRALIA",
            "INDIA","GERMANY",
            "RUSSIA","SPAIN",
            "TURKEY","UK"
    };
    Integer[] imgid= new Integer[]{
            R.drawable.america, R.drawable.australia,
            R.drawable.india, R.drawable.germany,
            R.drawable.russia, R.drawable.spain,
            R.drawable.turkey, R.drawable.uk
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        MyListAdapter adapter = new MyListAdapter(this, maintitle, imgid);
        list = findViewById(R.id.list);
        list.setAdapter(adapter);

        list.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                // TODO Auto-generated method stub
                if(position == 0) {
                    // code specific to first list item
                    Toast.makeText(getApplicationContext(),"Welcome to America",Toast.LENGTH_SHORT).show();
                } else if(position == 1) {
                    // code specific to the second list item
                    Toast.makeText(getApplicationContext(),"Welcome to Australia",Toast.LENGTH_SHORT).show();
                } else if(position == 2) {
                    Toast.makeText(getApplicationContext(),"Welcome to India",Toast.LENGTH_SHORT).show();
                } else if(position == 3) {
                    Toast.makeText(getApplicationContext(),"Welcome to Germany",Toast.LENGTH_SHORT).show();
                } else if(position == 4) {
                    Toast.makeText(getApplicationContext(),"Welcome to Russia",Toast.LENGTH_SHORT).show();
                } else if(position == 5) {
                    Toast.makeText(getApplicationContext(),"Welcome to Spain",Toast.LENGTH_SHORT).show();
                } else if(position == 6) {
                    Toast.makeText(getApplicationContext(),"Welcome to Turkey",Toast.LENGTH_SHORT).show();
                } else if(position == 7) {
                    Toast.makeText(getApplicationContext(),"Welcome to UK",Toast.LENGTH_SHORT).show();
                }
            }
        });
    }
}

```

### OUTPUT:


![](https://github.com/KATHIR1611/EXP-7-MAD/blob/main/nm%202.png)


### RESULT:

Thus a Simple Android Application to create and develop the application to display the place name with image using list view in android studio is developed and executed successfully.
