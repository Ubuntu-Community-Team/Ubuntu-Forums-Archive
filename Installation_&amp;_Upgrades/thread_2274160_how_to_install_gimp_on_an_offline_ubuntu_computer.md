---
title: "how to install gimp on an offline ubuntu computer?"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by newbie14 on 2015-04-18
I am running ubuntu 14.04 LTS "Trusty", and installed ubuntu on a flash drive using this tutorial: 
[http://ubuntuforums.org/showthread.php?t=2272475](http://ubuntuforums.org/showthread.php?t=2272475)

And I want to install gimp image editor.

[B]SOLUTION:
[/B]
**step 1:** install synaptic using this tutorial:
[http://ubuntuforums.org/showthread.php?t=2269294&p=13245493#post13245493](http://ubuntuforums.org/showthread.php?t=2269294&p=13245493#post13245493)

[**step 2:**]("http://i.imgur.com/bVk7C0m.jpg") open synaptic.

[**step 3:**]("http://i.imgur.com/xBlz4oL.jpg") type in "gimp" in the "quick filter" search box.

[**step 4:**]("http://i.imgur.com/8hn7bvv.jpg") left click the check box that has "gimp" written by the box' side, until a floating menu appears. And then left click the "mark for installation" option on the floating menu.

[**step 5:**]("http://i.imgur.com/ifGE0ao.jpg") a "synaptic" dialog box will appear, left click the "mark" button.

[**step 6:**]("http://i.imgur.com/WiCcuER.jpg") on the menu bar, left click "file" option, and then left click "generate package download script" option.

[**step 7:**]("http://i.imgur.com/aUU3f6E.jpg") a "save script" dialog box will appear, left click the name of the flash drive in the directory tree box, and then type in the name of the script file at the "name" text box. And then left click the "save" button.

**[step 8]("http://i.imgur.com/LmHKW2i.jpg"): **Make sure the script file is in the flash drive. close synaptic, turn of offline ubuntu computer, go to an online windows computer, plug in the flash drive.

step 9: open the script file using notepad

[**step 10:**]("http://i.imgur.com/jlldUIh.jpg") highlight the text inside the file. make sure to highlight the text that looks like a proper u.r.l address (leave out anything before "http..." and anything after "....deb").

step 11: copy and paste each u.r.l address to browser and download each file.

step 12: go to these addresses and download each .deb file from each of these links:
[http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libamd2.3.1_4.2.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libamd2.3.1_4.2.1-3ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/b/babl/libbabl-0.1-0_0.1.10-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/babl/libbabl-0.1-0_0.1.10-1ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcamd2.3.1_4.2.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcamd2.3.1_4.2.1-3ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libccolamd2.8.0_4.2.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libccolamd2.8.0_4.2.1-3ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/b/blas/libblas3_1.2.20110419-7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/blas/libblas3_1.2.20110419-7_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libgfortran3_4.8.2-19ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libgfortran3_4.8.2-19ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/l/lapack/liblapack3_3.5.0-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lapack/liblapack3_3.5.0-2ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcholmod2.1.2_4.2.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libcholmod2.1.2_4.2.1-3ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/i/ilmbase/libilmbase6_1.0.1-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/ilmbase/libilmbase6_1.0.1-6ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr6_1.6.1-7ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr6_1.6.1-7ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15-8ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2debian_1.2.15-8ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libumfpack5.6.2_4.2.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/suitesparse/libumfpack5.6.2_4.2.1-3ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gegl/libgegl-0.2-0_0.2.0-4ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gegl/libgegl-0.2-0_0.2.0-4ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.0-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.0-1ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng2_2.0.2-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng2_2.0.2-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.0-1ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-common_2.4.0-1ubuntu2_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-0_2.4.0-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libwebkitgtk-1.0-0_2.4.0-1ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.8.10-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.8.10-0ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.8.10-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.8.10-0ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.8.10-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.8.10-0ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-common_2.6.1-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-common_2.6.1-1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2.6.1-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp-help/gimp-help-en_2.6.1-1_all.deb)

step 13: copy all downloaded files to a flash drive.
step 14: paste all .deb files from flash drive to the home folder of the ubuntu computer
step 15: In the terminal, type in
```

sudo dpkg -i packagename.deb

```
where "packagename.deb is the name of the .deb file"
step 16: repeat step 4 and change the name of the .deb file.
step 17: open the gimp image editor by typing "gimp" in the terminal.

---

### Post by coffeecat on 2015-04-18
You are making life difficult for yourself by downloading and trying to compile the source code. The best way to install apps on an offline computer is to download needed .deb packages on an online computer. The trick is to find the complete list of dependencies so that you get all the .deb packages you need. Here is a community wiki page that may be helpful:

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

My preference would be to use the synaptic method. The download script it creates is a simple list of wget instructions, so if you have to use Windows it is easy to extract all the urls of the packages to be downloaded and download them one at a time in a browser. Be aware, though, that if you save the synaptic generated download script to a Linux filesystem, it will be owned by root.

---

### Post by ian-weisser on 2015-04-18
In a [different thread you started]("http://ubuntuforums.org/showthread.php?t=2269294") weeks ago, you asked how to install Synaptic on an offline computer.
We told you.

You install Gimp exactly the same way. All packaged software installs the same way. Just change the name of the package.
Simple installation is one of the reasons for packaging.

If you want to install using tarballs and source, you are welcome to...but they are not easy for beginners. Your troubles installing Gimp are an example of why the community moved away from those kinds of installs towards using packages.

---

### Post by newbie14 on 2015-04-28
Thanks everyone

---

