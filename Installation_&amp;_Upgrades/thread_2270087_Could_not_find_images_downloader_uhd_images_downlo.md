---
title: "Could not find images downloader: uhd_images_downloader.py in any of /usr/local/share"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by nur3 on 2015-03-20
[FONT=arial]i am use ubuntu 14.04 LTS. as i am installing gnuradio from this link:
[http://gnuradio.org/redmine/projects...ngGRFromSource]("http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGRFromSource")
[/FONT]
[FONT=arial](which install gnuradio &uhd) choose build from source


Done building/installing UHD
Done function uhd_build at: Jum Mac 20 16:57:06 MYT 2015
Starting function firmware at: Jum Mac 20 16:57:06 MYT 2015
Could not find images downloader: uhd_images_downloader.py in any of /usr/local/share /usr/local/lib /usr/local/lib64

what can i do. i hope you can help me
:cry:
[/FONT]

---

### Post by dino99 on 2015-03-20
you know, ubuntu is made for human  :p

purge gnuradio & uhd which you have tried to install (sudo apt-get purge gnuradio* && sudo apt-get purge uhd*)
then install it from the ubuntu archive (sudo apt-get install gnuradio)
that's all  ):P

---

### Post by Chuyan on 2015-03-21
Using Marcus Leech's script "build-gnuradio," I got the same error message while trying to  install gnuradio on Ubuntu 14.04.2 LTS. The message says that "uhd_images_dowloader.py" could not be found. When I did a file search, it was there under /usr/lib/uhd/utils. I copied the file over to /usr/local/share but it did not help.

When I tried to use "apt-get install gnuradio," I got a unmet dependencies issue concerning libCheese-gtk23 and libclutter-gtk etc.

Both ways failed. Appreciate any help to solve either of the above two problems so I could install gnuradio on Ubuntu.

---

### Post by nur3 on 2015-03-21
already try but it unable to locate package uhd
what can i do?i hope you can help me

---

### Post by SeijiSensei on 2015-03-21
First, let's see if uhd_images_downloader.py exists anywhere on your system:
```

sudo updatedb
locate uhd_images_downloader.py

```

---

### Post by nur3 on 2015-03-22
/build$ locate uhd_images_downloader.py
/home/userr/build/uhd/host/utils/uhd_images_downloader.py.in

when i try to locate,the uhd image downloader,it unable it.what can i do?i hope you can help me

---

### Post by Chuyan on 2015-03-22
I tried to install gnuradio on ubuntu14.04LTS and got the error messages:
sudo apt-get install gnuradio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 
 
I tried to solve the dependencies and got this:
 
chun@hp:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
I tried to install the 6 packages in questions individually (libcheese-gtk23, libcheese7 , libclutter-gtk-1.0-0, libcogl15, gstreamer1.0-clutter, libcogl15) and got the same message, which seems to tell me I have all the missing packages:
 
chun@hp:~$ sudo apt-get install libclutter-gtk-1.0.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libclutter-gtk-1.0-0' for regex 'libclutter-gtk-1.0.0'
libclutter-gtk-1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
But why gnuradio installation stopped and how to proceed? Please help here.
 
 
 
I also followed another method to install using the build-gnuradio script and a different error message:
 
wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio
Done building/installing UHD
Done function uhd_build at: Fri Mar 20 22:21:41 PDT 2015
Starting function firmware at: Fri Mar 20 22:21:41 PDT 2015
Could not find images downloader: uhd_images_downloader.py in any of /usr/local/share /usr/local/lib /usr/local/lib64
 
I searched my computer and actually found the file in /usr/lib/uhd/utils. I copied the file over to /usr/local/share and /usr/local/lib. But it still said it could not find it. Please help here.

---

