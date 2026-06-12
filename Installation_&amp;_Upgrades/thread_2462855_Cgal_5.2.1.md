---
title: "Cgal 5.2.1"
date: 2021-05-28
forum: Installation &amp; Upgrades
---

### Post by srsouza on 2021-05-28
Hi! I am using Ubuntu 20.04 LTS and I am trying to get CGAL-5.2.1 running. I followed the instructions on:

[https://doc.cgal.org/latest/Manual/installation.html](https://doc.cgal.org/latest/Manual/installation.html)

cd $HOME/CGAL-5.2.1
mkdir build
cd build
cmake -DCGAL_HEADER_ONLY=OFF -DCMAKE_BUILD_TYPE=Release ..                        # configure CGAL
make                                                                              # build CGAL
make install                                                                      # install CGAL
cd examples/Triangulation_2                                                       # go to an example directory
cmake -DCGAL_DIR=$CMAKE_INSTALLED_PREFIX/lib/CGAL -DCMAKE_BUILD_TYPE=Release .    # configure the examples
make                                                                              # build the examples

Everything is fine but when I run draw_Triangulation_2, I get the following error message:

Impossible to draw, CGAL_USE_BASIC_VIEWER is not defined.



Then, I follow the instructions on this thread

[https://stackoverflow.com/questions/53150670/impossible-to-draw-because-cgal-use-basic-viewer-is-not-defined](https://stackoverflow.com/questions/53150670/impossible-to-draw-because-cgal-use-basic-viewer-is-not-defined)

and put the line

[FONT=inherit]#CGAL_USE_BASIC_VIEWER
[/FONT]
[FONT=inherit]at the top of the file, run the Makefile again and receive the following error messages:

[ 84%] Building CXX object CMakeFiles/draw_triangulation_2.dir/draw_triangulation_2.cpp.o
In file included from /usr/local/include/CGAL/draw_triangulation_2.h:16,
                 from /home/srsouza/Dropbox/Valmir/Progs/Gastrulation/CGAL-5.2.1/examples/Triangulation_2/draw_triangulation_2.cpp:5:
/usr/local/include/CGAL/Qt/Basic_viewer_qt.h:30:10: fatal error: QApplication: No such file or directory
   30 | #include <QApplication>
      |          ^~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [CMakeFiles/draw_triangulation_2.dir/build.make:63: CMakeFiles/draw_triangulation_2.dir/draw_triangulation_2.cpp.o] Error 1
make[1]: *** [CMakeFiles/Makefile2:689: CMakeFiles/draw_triangulation_2.dir/all] Error 2
make: *** [Makefile:84: all] Error 2



Could anyone help me? Thanks![/FONT]

---

### Post by norobro on 2021-05-29
Try adding "-DCGAL_USE_BASIC_VIEWER" to your cmake line for the triangulation_2 example:```
cmake -DCGAL_DIR=$CMAKE_INSTALLED_PREFIX/lib/CGAL -DCMAKE_BUILD_TYPE=Release -DCGAL_USE_BASIC_VIEWER .
```Works fine on 21.04 which has CGAL-5.2.1 in the repros. If you need 5.2.1 you might consider upgrading. [https://packages.ubuntu.com/hirsute/libcgal-dev](https://packages.ubuntu.com/hirsute/libcgal-dev) ```
~/Downloads/cgal/examples/Triangulation_2/build$ ldd draw_triangulation_2 | grep Qt
    libQt5OpenGL.so.5 => /lib/x86_64-linux-gnu/libQt5OpenGL.so.5 (0x00007ff5fcfd3000)
    libQt5Svg.so.5 => /lib/x86_64-linux-gnu/libQt5Svg.so.5 (0x00007ff5fcf76000)
    libQt5Widgets.so.5 => /lib/x86_64-linux-gnu/libQt5Widgets.so.5 (0x00007ff5fc8d6000)
    libQt5Gui.so.5 => /lib/x86_64-linux-gnu/libQt5Gui.so.5 (0x00007ff5fc206000)
    libQt5Xml.so.5 => /lib/x86_64-linux-gnu/libQt5Xml.so.5 (0x00007ff5fc1c1000)
    libQt5Core.so.5 => /lib/x86_64-linux-gnu/libQt5Core.so.5 (0x00007ff5fbc67000)

```

---

### Post by srsouza on 2021-06-08
Thanks for the reply with the detailed instructions. However, it did not work for me. I still have the same error message and when I run ldd I get:


        linux-vdso.so.1 (0x00007ffd73bb9000)
        libCGAL.so.13 => /usr/local/lib/libCGAL.so.13 (0x00007f8db0f84000)
        libgmp.so.10 => /lib/x86_64-linux-gnu/libgmp.so.10 (0x00007f8db0eed000)
        libstdc++.so.6 => /lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f8db0d0c000)
        libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f8db0cf1000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f8db0aff000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f8db0fac000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f8db09b0000)


It seems that Qt5 is not installed, but I checked that they are indeed. Any further suggestions?

---

### Post by norobro on 2021-06-11
> **srsouza said:**
> [FONT=inherit]/usr/local/include/CGAL/Qt/Basic_viewer_qt.h:30:10: fatal error: QApplication: No such file or directory
   30 | #include <QApplication>
      |          ^~~~~~~~~~~~~~
compilation terminated.
[/FONT]The above indicates that the compiler can't locate the Qt5 header files.

 Do you have qtbase5-dev installed? [https://packages.ubuntu.com/focal/qtbase5-dev](https://packages.ubuntu.com/focal/qtbase5-dev)

---

### Post by monkeybrain20122 on 2021-06-13
cgal has a lot of options, instead using cmake to confiigure, use the cmake gui, inside the build directory

```
ccmake ..
```


then you can see all the options and toggle to activate them. This way you get more legible feedback.

---

### Post by srsouza on 2021-06-18
Thanks for the reply. I finally got it working, although through a noncanonical path...

I installed:

1) debian10.9,
2) anaconda3 (open source)
[https://www.anaconda.com](https://www.anaconda.com)
3) The libraries: [COLOR=#000000][FONT=Menlo]libqt5opengl5-dev libgmp-dev libmpfr-dev libboost-dev libeigen3-dev [/FONT][/COLOR][FONT=Menlo][COLOR=#000000]libqt5opengl5-dev[/COLOR][/FONT]

[FONT=Menlo][COLOR=#000000]and it finally worked!
 
Thank you all for the help.[/COLOR][/FONT]

---

