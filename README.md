# Tugas-Pert12

Nama : Zulaeha

NIM : 312210575

Kelas : TI.22.A5

Mata Kuliah : Pemrograman Mobile 1

Dosen Pengampu : Donny Maulana, S.Kom.,M.M.S.I.

## Tugas

<img width="603" alt="tugasfragment" src="https://github.com/zulaeha168/Tugas-Pert12/assets/130324650/63846bf6-505b-456e-9ff5-741456108f00">

## Fill in All The Code in This Project :
> 1. ***Gradle Script*** => `build.gradle.kts (Module :app)`
```
plugins {
    id("com.android.application")
}
android {
    namespace = "com.tabexperiment"
    compileSdk = 34
    defaultConfig {
        applicationId = "com.tabexperiment"
        minSdk = 21
        targetSdk = 33
        versionCode = 1
        versionName = "1.0"
        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }
    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"), "proguard-rules.pro")
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    buildToolsVersion = "34.0.0"
}
dependencies {
    val fragment_version = "1.6.1"
    implementation("androidx.appcompat:appcompat:1.6.1")
    implementation("com.google.android.material:material:1.10.0")
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")
    testImplementation("junit:junit:4.13.2")
    androidTestImplementation("androidx.test.ext:junit:1.1.5")
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")
    implementation("androidx.fragment:fragment:$fragment_version")
}
```
- Setelah itu klik `Sync now`
> 2. ***java***
=> `MainActivity.java`
```
package com.example.fragment;
import androidx.appcompat.app.AppCompatActivity;
import androidx.viewpager2.widget.ViewPager2;
import android.annotation.SuppressLint;
import android.graphics.drawable.ColorDrawable;
import android.os.Bundle;
import com.google.android.material.tabs.TabLayout;
import java.util.Objects;
public class MainActivity extends AppCompatActivity {
    TabLayout tabLayout;
    ViewPager2 viewPager2;
    ViewAdapter adapter;
    @SuppressLint("NewApi")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Objects.requireNonNull(getSupportActionBar()).setBackgroundDrawable(new ColorDrawable(getColor(R.color.hijautua)));
        tabLayout = findViewById(R.id.tab);
        viewPager2 = findViewById(R.id.view);
        adapter = new ViewAdapter(this);
        viewPager2.setAdapter(adapter);
        tabLayout.addOnTabSelectedListener(new TabLayout.OnTabSelectedListener() {
            @Override
            public void onTabSelected(TabLayout.Tab tab) {
                viewPager2.setCurrentItem(tab.getPosition());
            }
            @Override
            public void onTabUnselected(TabLayout.Tab tab) {
            }
            @Override
            public void onTabReselected(TabLayout.Tab tab) {
            }
        });
        viewPager2.registerOnPageChangeCallback(new ViewPager2.OnPageChangeCallback() {
            @Override
            public void onPageSelected(int position) {
                super.onPageSelected(position);
                tabLayout.getTabAt(position).select();
            }
        });
    }
}
```
=> Membuat file fragment dengan cara klik kanan pada `MainActivity.java` lalu pilih dan klik fragment, setelah itu kita pilih dan klik fragment (Blank), setelah itu kita beri nama `ActionFragment`, `HororFragment`, `RomanceFragment`. Untuk file fragment sudah sekaligus dengan file layout xml nya (code berada pada bagian res `layout`)
- `ActionFragment.java` :
```
package com.example.fragment;
import android.os.Bundle;
import androidx.fragment.app.Fragment;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;
public class ActionFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_action, container, false);
    }
    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_action) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```
- `HororFragment.java` :
```
package com.example.fragment;
import android.os.Bundle;
import androidx.fragment.app.Fragment;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;
public class HororFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_horor, container, false);
    }
    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_horor) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```
- `RomanceFragment.java` :
```
package com.example.fragment;
import android.os.Bundle;
import androidx.fragment.app.Fragment;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Toast;
public class RomanceFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        return inflater.inflate(R.layout.fragment_romance, container, false);
    }
    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_romance) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }
}
```
=> Lalu buat java class dengan nama `ViewAdapter.java`, yang berisi code :
```
package com.example.fragment;
import androidx.annotation.NonNull;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentActivity;
import androidx.viewpager2.adapter.FragmentStateAdapter;
public class ViewAdapter extends FragmentStateAdapter {
    public ViewAdapter(@NonNull FragmentActivity fragmentActivity) {
        super(fragmentActivity);
    }
    @NonNull
    @Override
    public Fragment createFragment(int position) {
        switch (position){
            case 0:
                return new ActionFragment();
            case 1:
                return new Horor Fragment();
            case 2:
                return new RomanceFragment();
            default:
                return new ActionFragment();
        }
    }
    @Override
    public int getItemCount() {
        return 3;
    }
}
```
> 3. ***res***
=> `values`
- `Colors.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="cream">#E6C18A</color>
    <color name="coklat">#65362c</color>
    <color name="abu">#B0B0B2</color>
    <color name="tosca">#70AE98</color>
    <color name="soft">#AED9EA</color>
    <color name="pastel">#5E96AE</color>
</resources>
</resources>
```
=> `themes`
- `themes.xml` dan `themes.xml(night)` (sama isi code nya) :
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Base.Theme.fragment" parent="Theme.MaterialComponents.DayNight.DarkActionBar">
        <!-- Primary brand color. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryVariant">@color/hijaumuda</item>
        <item name="colorOnPrimary">@color/white</item>
        <!-- Secondary brand color. -->
        <item name="colorSecondary">@color/pastel</item>
        <item name="colorSecondaryVariant">@color/soft</item>
        <item name="colorOnSecondary">@color/black</item>
        <!-- Status bar color. -->
        <item name="android:statusBarColor">@color/purple</item>
        <item name="android:navigationBarColor">@color/purple</item>
        <!-- Customize your light theme here. -->
    </style>

    <style name="Theme.TabExperiment" parent="Base.Theme.TabExperiment" />
</resources>
```
=> `layout`
- `activity_main.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/white"
    tools:context=".MainActivity">


    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tab"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/pastel"
        app:tabSelectedTextColor="@color/white"
        app:tabIndicatorColor="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="3dp"
        tools:ignore="MissingConstraints">

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Action"
            tools:layout_editor_absoluteX="0dp"
            tools:layout_editor_absoluteY="3dp" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Comedy" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Romance" />
    </com.google.android.material.tabs.TabLayout>

    <androidx.viewpager2.widget.ViewPager2
        android:id="@+id/view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginTop="50dp"
        android:background="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="52dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- `fragment_action.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ActionFragment">

    <!-- TODO: Update blank fragment layout -->

    <TextView
        android:id="@+id/action_sinopsis"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:text="Sinopsis film : Batman, letnan polisi James Gordon, dan jaksa wilayah Harvey Dent, yang membentuk aliansi untuk membongkar kejahatan terorganisir di Kota Gotham. Upaya mereka digagalkan oleh Joker, dalang anarkis yang berusaha menguji seberapa jauh Batman akan pergi untuk menyelamatkan kota dari kekacauan.Lalu Lau disembunyikan sebelum melarikan diri ke Hong Kong untuk menghindari ekstradisi.Dengan bantuan CEO Wayne Enterprises Lucius Fox, Batman menemukan Lau di Hong Kong dan mengembalikannya ke tahanan polisi Gotham. Gordon menyelamatkan walikota, Joker mengancam serangannya akan berlanjut sampai Batman mengungkapkan identitasnya. Dia menargetkan Dent saat makan malam penggalangan dana dan melempar Rachel keluar jendela, tapi Batman menyelamatkannya."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="15sp"
        android:textStyle="bold"
        android:textColor="@color/black"/>

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="200dp"
        android:layout_height="1000dp"
        android:src="@drawable/filmaction" />
</FrameLayout>
```
- `fragment_horor.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HororFragment">

    <!-- TODO: Update blank fragment layout -->

    <TextView
        android:id="@+id/action_sinopsis"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:text="Sinopsis film : Film ini mengangkat mitos yang sudah lama dipercaya oleh sebagian besar masyarakat Indonesia, yaitu tentang sakralnya waktu maghrib. Mitos ini relevan dengan kalangan para orang tua dan anak-anak. Jika anak-anak masih berada di luar rumah dan mangkir dari kewajiban beribadah saat waktu maghrib tiba, anak-anak tersebut akan diculik oleh hantu. 
Mitos tersebut direpresentasikan di dalam film ini dengan pendekatan yang sesuai dengan kehidupan sehari-hari. Karena itu, diharapkan film ini dapat membuat setiap penontonnya merasa relate dan dapat mengambil nilai moral yang ada di film WAKTU MAGHRIB."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="15sp"
        android:textStyle="bold"
        android:textColor="@color/black"/>

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="200dp"
        android:layout_height="1029dp"
        android:src="@drawable/filmhoror" />
</FrameLayout>
```
- `fragment_romance.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".RomanceFragment">

    <!-- TODO: Update blank fragment layout -->

    <ImageView
        android:id="@+id/imageView3"
        android:layout_width="200dp"
        android:layout_height="1009dp"
        android:src="@drawable/filmromance" />

    <TextView
        android:id="@+id/romance_sinopsis"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Sinopsis film : Film ini bercerita tentang seorang remaja SMA bernama Nathan (Jefri Nichol) yang bertemu dengan Salma Avira (Amanda Rawles), akibat keterlambatan mereka mengikuti upacara pertama di sekolah baru.Nathan membantu Salma untuk masuk ke sekolah dengan menggunakan jalan pintas dan menghindarkan Salma dari hukuman.Nathan terkenal sebagai siswa yang nakal dan sering ikut tawuran di sekolah. Berbeda dengan Salma yang memiliki pergaulan baik dan juga tahu batasan dalam pergaulan. Namun hal ini malah membuat keduanya makin akrab.Suatu waktu Nathan mengakui perasaannya kepada Salma dan berusaha untuk mendapatkan hatinya. Awalnya Salma menolak, namun Salma akhirnya menaruh simpati kepada Nathan setelah tahu kerapuhan masa lalu Nathan.Akhirnya mereka saling jatuh cinta dan Salma membantu Nathan untuk menjadi pribadi yang lebih baik. Namun permasalahan muncul, pasalnya mantan kekasih Nathan hadir kembali ke kehidupan Nathan."
        android:textAlignment="viewStart"
        android:textAppearance="@style/TextAppearance.AppCompat.Display1"
        android:textSize="15sp"
        android:textStyle="bold"
        android:textColor="@color/black"/>

</FrameLayout>
```
=> Pada directory `drawable` kita bisa tambahkan gambar untuk pict dari film yang ingin kita tampilkan, dan jangan lupa untuk menambahkan icon `baseline_more_vert_24.xml` dengan cara klik kanan pada `drawable` lalu klik New, setelah itu kita pilih dan klik Vector Asset. Setelah itu kita klik clip art lalu kita pilih icon nya, jika sudah ketemu kita klik OK lalu kita klik next
=> Selanjutnya kita klik kanan pada `app` lalu pilih dan klik `Android Resource Directory` setelah itu kita beri nama "menu" lalu klik OK. Setelah itu kita buat Menu Resource File dengan nama `menu_tab.xml` lalu isi dengan code :
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/tab_action"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Action"/>
    <item
        android:id="@+id/tab_horor"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Comedy"/>
    <item
        android:id="@+id/tab_romance"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Romance"/>
</menu>
```

> Hasil Run :

https://github.com/zulaeha168/Tugas-Pert12/assets/130324650/d79865df-458d-4337-8687-7cfc3b6f6864




## Selesai, Terima Kasih 
