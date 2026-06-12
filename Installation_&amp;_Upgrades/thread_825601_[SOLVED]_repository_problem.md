---
title: "[SOLVED] repository problem?"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-06-11
I am trying to install the required software for my UPS. They have a dedicated "Ubuntu" distribution.:)
I followed their instructions and added "deb [http://opensource.mgeops.com/stable/debian](http://opensource.mgeops.com/stable/debian) binary/" to the list of repositories.
Then I used the root terminal and ran "apt-get update", which updated the list.
Then I did "apt-get install mgeops-psp" which returned the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mgeops-psp

On inspection of the previous update transcript I noticed the following lines relating to mgeops

Ign [http://opensource.mgeops.com](http://opensource.mgeops.com) binary/ Release.gpg
Ign [http://opensource.mgeops.com](http://opensource.mgeops.com) binary/ Translation-en_AU
Ign [http://opensource.mgeops.com](http://opensource.mgeops.com) binary/ Release
Ign [http://opensource.mgeops.com](http://opensource.mgeops.com) binary/ Packages
Hit [http://opensource.mgeops.com](http://opensource.mgeops.com) binary/ Packages

From this I assume that most parts were not updated?

I have since downloaded their mgeops-psp.tar.gz which has a heap of files and directories in it.
Can I manually place these files and where?:confused:

---

### Post by Partyboi2 on 2008-06-11
I just tried it, and installed the package, maybe retry again and see what happens

---

### Post by Stolea on 2008-06-11
Just tried it again, same result :(
a mate of mine tried it and it worked just fine for him.
Can I install it via the tar.gz, and where do I extract it to?

---

### Post by Partyboi2 on 2008-06-11
make sure you have build-essential. Open  a terminal 
```
sudo apt-get install build-essential
```
then change directory to where you have the downloaded mgeops-psp.tar.gz file.
(If its on your desktop) 
```
cd Desktop
```
then extract it with
```
tar xvzf mgeops-psp.tar.gz
```then cd into the newly created directory. eg. ```
cd mgeops-psp
``` then type
```
./configure
``` and make sure you have all dependencies met.
then
```
make
```
then finally
```
sudo make install
```
All going well it should then be installed.

---

### Post by forger on 2008-06-11
> deb [http://opensource.mgeops.com/stable/debian](http://opensource.mgeops.com/stable/debian) binary/
I think that "/" at the end is the problem, try:
> deb [http://opensource.mgeops.com/stable/debian](http://opensource.mgeops.com/stable/debian) binary

alternative way:
[http://opensource.mgeops.com/stable/debian/binary/mgeops-psp_3.0.6-4_i386.deb](http://opensource.mgeops.com/stable/debian/binary/mgeops-psp_3.0.6-4_i386.deb)
[http://opensource.mgeops.com/stable/debian/binary/nut_2.2.0-2_i386.deb](http://opensource.mgeops.com/stable/debian/binary/nut_2.2.0-2_i386.deb)

download and double click on them :)

---

### Post by Stolea on 2008-06-11
I got as far as the ./configure and at the end of the process and multitudes of processes it said 
[COLOR="Navy"]
checking pkg-config is at least version 0.9.0... yes
checking for NUT... configure: error: Package requirements (libupsclient >= 2.0.0) were not met:

No package 'libupsclient' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NUT_CFLAGS
and NUT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/COLOR]

when I then type "make" it says

[COLOR="Navy"]make: *** No targets specified and no makefile found.  Stop.[/COLOR]

?????

---

### Post by Pumalite on 2008-06-11
This might help:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Partyboi2 on 2008-06-11
try installing nut-dev package
```
sudo apt-get install nut-dev
```
then retry
```
./configure
```

---

### Post by Stolea on 2008-06-11
Well this time I got a different message:

[COLOR="Blue"]checking for NUT... yes
checking for GTKMM... configure: error: Package requirements (gtkmm-2.4 >= 2.4.5) were not met:

No package 'gtkmm-2.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKMM_CFLAGS
and GTKMM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/COLOR]

I assume I am missing another module or something?

---

### Post by Partyboi2 on 2008-06-11
When you run the ./configure command and see anything  like
> [COLOR=Blue] No package 'gtkmm-2.4' found[/COLOR] It means that you need to install that package that is mentioned. So a good place to look for the packages you need is from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") making sure that you use the packages ending -dev. Sometimes it can be trial and error till you find the correct one. So the package you now need to install is```
 libgtkmm-2.4-dev

``` then rerun ./configure

---

### Post by Stolea on 2008-06-11
Lol,
Now I am getiing this message:

[COLOR="Blue"]checking for NUT... yes
checking for GTKMM... yes
checking for GTHREAD... yes
checking for libusb... configure: error: not found

peter@shop:~/temp/mgeops-psp-3.0.7$ make
make: *** No targets specified and no makefile found.  Stop.[/COLOR]

I take it some other part is missing. How can I tell what the missing file is called?

---

### Post by Partyboi2 on 2008-06-11
try ```
sudo apt-get install libusb-dev
```
if ./configure returns with no errors then proceed onto make

---

### Post by Stolea on 2008-06-12
Thank you very much. This time it worked, but as with my graphics card it doesn't work. I am wondering about this bit of machinery. Works fine with Windoze, but it seems to do weird things with Ubuntu.
The fact that you could do the install as set out by MGE but I could not is a worry. I had the same sort of hassles with my ATI Radeon 9550 card when I tried to use the ATI driver. All I can get is a white screen, and for some reason the Mesa driver won't let go. I had no end of hassles with my network with other computers. After endless attemps at least now I can connect to my other computer, but it won't auto mount, no matter what. As yet I haven't been able to set up any shares, says it can't change the permissions of the share?? Its like the hardware is just not talking to each other, but at least its consistent in that.
I like Ubuntu and am determined to stay with it, but boy, its a learning curve and a half. Even for someone who has been working with computers for 22 years. :)
I am running the 64 bit version as its an AMD64/3000 chip on a Gigabyte GA-K8NSC-939 board with 2 gig RAM and 200g HD dedicated to Ubuntu. So its not lacking resources, but for some reason it has harware issues.

---

### Post by Stolea on 2008-06-12
I was just trying to uninstall the software and at the end of the uninstall it returned the following:

[COLOR="Blue"]Broadcast Message from nut@shop                                                
        (somewhere) at 17:49 ...                                               
                                                                               
UPS mgeups@localhost is unavailable [/COLOR]

I assume that means that the system can't even see the UPS. I have tried a different USB port without any change in report. As I said, it would appear that parts of my computer don't want to talk to other parts?

---

