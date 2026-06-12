---
title: "Trying to install Guitar Pro 6 on 64-bit, issue with libraries"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by robawalsh on 2012-06-07
I have Ubuntu 12.04 LTS 64-bit on both my laptop and my desktop. 
  I managed to install Guitar Pro 6 on my desktop by using 32-bit dependencies, following the instructions [here]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/how_to_install_gp6_from_the_demo_deb_in_ubuntu_11_10_64_bits") to install: 
  I followed the exact same methods on my laptop, but Guitar Pro 6 won't run.  I have tried the official demo from the website, which didn't work either. 
  When downgrading my libraries to 32-bit for Guitar Pro 6 install, at  some point in the terminal it had an issue with LibGL, saying it was  installed by the video driver. 
  I suspect this may be the cause of the problem, since after Googling  for hours, the only issues were with libportaudio, which I downgraded  successfully. 
  So, is there a way to downgrade LibGL to 32-bit, since it is  installed with the video driver? Would this stop my display working, or  is it impossible? 

  --

  I also tried installing the Windows version under Wine and  PlayOnLinux, neither of which worked. Guitar Pro 6 installs  successfully, but then nothing happens when I try to run it. 
  If I am wrong about LibGL, does anyone know a way I could get Guitar  Pro 6 working? I desperately need it to work, and don't want to  downgrade to 32-bit. 


  **UPDATE: I ran /opt/GuitarPro6 !$ ldd ./GuitarPro and it reported that libGL.so.1 was 'not found' I found the file(s) in the nvidia-current directory, and placed them in /usr/lib/i386-linux-gnu/mesa/ The issue now is, how can I tell Guitar Pro 6 where to find them?**
      

```

robawalsh@Dell-Inspiron-N5110:~$ cd /opt/GuitarPro6
robawalsh@Dell-Inspiron-N5110:/opt/GuitarPro6$ ldd ./GuitarPro
    linux-gate.so.1 =>  (0xf778d000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7769000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf7684000)
    libGL.so.1 => not found
    libGPCore.so => ./libGPCore.so (0xf71fa000)
    libOverLoud.so => ./libOverLoud.so (0xf7067000)
    libPickupModeling.so => ./libPickupModeling.so (0xf7035000)
    libRSEAudioCore.so => ./libRSEAudioCore.so (0xf701d000)
    libRSECore.so => ./libRSECore.so (0xf6ebc000)
    libWavFile.so => ./libWavFile.so (0xf6eae000)
    libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf6dbc000)
    libboost_filesystem-gcc43-mt-1_39.so.1.39.0 => ./libboost_filesystem-gcc43-mt-1_39.so.1.39.0 (0xf6da7000)
    libboost_system-gcc43-mt-1_39.so.1.39.0 => ./libboost_system-gcc43-mt-1_39.so.1.39.0 (0xf6da2000)
    libboost_thread-gcc43-mt-1_39.so.1.39.0 => ./libboost_thread-gcc43-mt-1_39.so.1.39.0 (0xf6d8c000)
    libchunk.so => ./libchunk.so (0xf6d88000)
    libexception.so => ./libexception.so (0xf6d84000)
    libfactory.so => ./libfactory.so (0xf6d7b000)
    libfilesystem.so => ./libfilesystem.so (0xf6d54000)
    libmemory.so => ./libmemory.so (0xf6d45000)
    libmmap.so => ./libmmap.so (0xf6d41000)
    libobject.so => ./libobject.so (0xf6d3b000)
    libportaudio.so.2 => /usr/lib/i386-linux-gnu/libportaudio.so.2 (0xf6d0d000)
    libprofiler.so => ./libprofiler.so (0xf6d05000)
    libpulse.so.0 => /usr/lib/i386-linux-gnu/libpulse.so.0 (0xf6cb6000)
    libpulse-simple.so.0 => /usr/lib/i386-linux-gnu/libpulse-simple.so.0 (0xf6cb1000)
    libregister.so => ./libregister.so (0xf6c9e000)
    libthread.so => ./libthread.so (0xf6c8a000)
    libtimer.so => ./libtimer.so (0xf6c86000)
    libvariant.so => ./libvariant.so (0xf6c74000)
    libxml.so => ./libxml.so (0xf6c66000)
    libQtCore.so.4 => ./libQtCore.so.4 (0xf69be000)
    libQtGui.so.4 => ./libQtGui.so.4 (0xf5edd000)
    libQtNetwork.so.4 => ./libQtNetwork.so.4 (0xf5dae000)
    libQtOpenGL.so.4 => ./libQtOpenGL.so.4 (0xf5cdc000)
    libQtSvg.so.4 => ./libQtSvg.so.4 (0xf5c84000)
    libQtXmlPatterns.so.4 => ./libQtXmlPatterns.so.4 (0xf580c000)
    libQtXml.so.4 => ./libQtXml.so.4 (0xf57c3000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf5797000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf5778000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf55d3000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf549f000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf5484000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf547a000)
    /lib/ld-linux.so.2 (0xf778e000)
    libxml2.so.2 => /usr/lib/i386-linux-gnu/libxml2.so.2 (0xf532c000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf5323000)
    libboost_date_time-gcc43-mt-1_39.so.1.39.0 => ./libboost_date_time-gcc43-mt-1_39.so.1.39.0 (0xf5311000)
    libjack.so.0 => /usr/lib/i386-linux-gnu/libjack.so.0 (0xf52cb000)
    libjson.so.0 => /usr/lib/i386-linux-gnu/libjson.so.0 (0xf52c3000)
    libpulsecommon-1.1.so => /usr/lib/i386-linux-gnu/libpulsecommon-1.1.so (0xf525e000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf5215000)
    libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0xf5211000)
    libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf5118000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf507e000)
    libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf502f000)
    libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf5026000)
    libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf500b000)
    libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf4fd7000)
    libz.so.1 => /opt/GuitarPro6/./libz.so.1 (0xf4fc1000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf4faf000)
    libGL.so.1 => not found
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf4f8d000)
    libwrap.so.0 => /lib/i386-linux-gnu/libwrap.so.0 (0xf4f83000)
    libsndfile.so.1 => /usr/lib/i386-linux-gnu/libsndfile.so.1 (0xf4f11000)
    libasyncns.so.0 => /usr/lib/i386-linux-gnu/libasyncns.so.0 (0xf4f0a000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf4ecd000)
    libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf4ec6000)
    libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xf4ec0000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf4e96000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf4e92000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf4e8a000)
    libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xf4e70000)
    libFLAC.so.8 => /usr/lib/i386-linux-gnu/libFLAC.so.8 (0xf4e22000)
    libvorbisenc.so.2 => /usr/lib/i386-linux-gnu/libvorbisenc.so.2 (0xf4caa000)
    libvorbis.so.0 => /usr/lib/i386-linux-gnu/libvorbis.so.0 (0xf4c7f000)
    libogg.so.0 => /usr/lib/i386-linux-gnu/libogg.so.0 (0xf4c76000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf4c5e000)
robawalsh@Dell-Inspiron-N5110:/opt/GuitarPro6$ 

```I think the problem is the
```
    libGL.so.1 => not found
```How can I fix this? 

I ran the ldd command on my desktop (on which Guitar Pro works) and noted where the file was. I copied the file and placed it in the same directory on my laptop. 
But the ldd command still reports "    libGL.so.1 => not found"

---

### Post by robawalsh on 2012-06-07
**UPDATE**

Using getlibs to try to install the library: 

```
robawalsh@Dell-Inspiron-N5110:~$ sudo getlibs -l libGL.so.1
[sudo] password for robawalsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libportsmf0 libflac++6 audacity-data libvamp-hostsdk3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**libGL is installed from video drivers, please install or reinstall your video drivers**
No packages to install
robawalsh@Dell-Inspiron-N5110:~$ 

```I want to avoid reinstalling video drivers, since my laptop has nvidia Optimus and so the only way I could get the display working correctly was with Bumblebee. 
If I reinstall the video drivers, my display might mess up.

---

### Post by robawalsh on 2012-06-07
Any ideas?

---

### Post by robawalsh on 2012-06-08
bump

---

### Post by robawalsh on 2012-06-09
145 views and not one response.

---

### Post by robawalsh on 2012-06-11
Since nobody here replied, I worked it out myself. 

If anyone else is trying to run Guitar Pro 6 on a laptop with NVIDIA Optimus (with Bumblebee drivers), the libGL.so.1 library is located in a different directory than what Guitar Pro expects. 

So, to tell it to search the correct directory each time you start it, edit the file "gp-launcher.sh" in "/opt/GuitarPro6" with *gedit* and add these two lines to the **top **of the file: 
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current
export LD_LIBRARY_PATH

```

Save the file and close. 

Then press ALT + F2 (if using GNOME) and type "alacarte". Find Guitar Pro 6 (under Sound & Video) and click properties. Click Browse and navigate back to /opt/GuitarPro6 and select gp-launcher.sh

Guitar Pro 6 should now run.

---

### Post by adam.d.clemons on 2012-08-06
Just wanted to say thank you and add a little bit of information to this post. I also had trouble installing GP6 on 12.04 64bit. 

I am running an HP Probook 4430s and I have the intel graphics, not the Nvidia. With the help of this post and a bit of enginuity I got GP6 working like a charm. To get GP6 working, I had to do the following.

```

sudo apt-get install ia32-libs
sudo apt-get install qtconfig-qt4 
sudo dpkg --force-depends -i gp6-full-linux-demo-rxxxxxx.deb

```

This broke my packages list so I ran 
```

sudo apt-get install -f

```

This removed GP6, but it installed the libsound library I needed.

```

sudo dpkg --force-depends -i gp6-full-linux-demo-rxxxxxx.deb
cd /opt/GuitarPro6
./GuitarPro

```

Guitar Pro now runs, but my packages are still broken, so I updated and activated guitar pro. Then I did the following.

```

sudo cp -r /opt/GuitarPro6 /home/user/GuitarPro6
sudo apt-get install -f
sudo rm -rf /opt/GuitarPro6
sudo cp -r /home/user/GuitarPro6 /opt/GuitarPro6

```

Now all you need is the desktop file! 

Save this to a .desktop file in ~/.local/shares/applications

```

#!/usr/bin/env xdg-open
[Desktop Entry]
Type=Application
Name=GuitarPro6
Comment=Best Guitar Tabulature Software Evrar!
Exec=/opt/GuitarPro6/GuitarPro
Path=/opt/GuitarPro6/
Icon=/opt/GuitarPro6/GP6.png
Terminal=false
Categories=Audio;
StartupNotify=false

```

I grabbed my icon from deviant art, the GP6.png doesn't exist by default.

Enjoy! I hope this helps other people who have this issue.

---

### Post by mgman on 2012-09-26
Thanks for this very useful thread.:)

---

