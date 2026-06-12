---
title: "Mail-notification and SSL issue (Update 9.10 Karmic)"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by mack75 on 2009-11-24
Hi:

Today I've upgraded my Ubuntu on my Laptop to 9.10 with a fresh installation.

I'm using the mail-notification program to checkout my inboxes, but, I prefer to use SSL to do that.

Previously I had used the short howto from this thread [http://ubuntuforums.org/showthread.php?t=589115]("http://ubuntuforums.org/showthread.php?t=589115") but today it didn't work.

So, I had to work on it.

Here some instructions to append at the short howto:

_Original Howto:_

cd /tmp
apt-get source mail-notification
sudo apt-get build-dep mail-notification
sudo apt-get install libssl-dev fakeroot
cd mail-notification-4.1.dfsg.1
vi debian/rules (remove --disable-ssl in line 11)
dpkg-buildpackage -rfakeroot
sudo cp debian/mail-notification/usr/bin/mail-notification /usr/bin/mail-notification

**_Modified Howto:_**
cd /tmp
apt-get source mail-notification

[COLOR="Blue"]We'll need some packages to build the dependencies:
+ [libeel2]("https://launchpad.net/ubuntu/jaunty/i386/libeel2-2/2.26.0-0ubuntu2")
+ [libeel2-data]("https://launchpad.net/ubuntu/jaunty/i386/libeel2-data/2.26.0-0ubuntu2")
+ [libeel2-dev]("https://launchpad.net/ubuntu/jaunty/i386/libeel2-dev/2.26.0-0ubuntu2")
Download all of them and install all of them with "dpkg -i"[/COLOR]

sudo apt-get build-dep mail-notification
sudo apt-get install libssl-dev fakeroot
cd mail-notification-5.4.dfsg.1 (thanks to rparker)
vi debian/rules ([COLOR="Blue"]in line 31 change the ssl=no to ssl=yes[/COLOR])

[COLOR="Blue"]Before to compile we need some packages:
sudo apt-get install gtkhtml3.8 libgtkhtml3.8-dev libgnomeprint2.2-dev libebook1.2-dev libgtkhtml-dev libgtkhtml-editor-dev

Now, we will make the symbolic links to avoid compilation errors:
cd /usr/include
sudo ln -s libgtkhtml-3.8/gtkhtml .
sudo ln -s libgnomeprint-2.2/libgnomeprint
sudo find libgtkhtml-3.14/editor/ -type f -exec ln -s {} . \;[/COLOR]

Now, we will build the package:

dpkg-buildpackage -rfakeroot

[COLOR="Blue"]Backup the original file:
sudo cp /usr/bin/mail-notification ~/mail-notification.ubuntu[/COLOR]

sudo cp debian/mail-notification/usr/bin/mail-notification /usr/bin/mail-notification

Enjoy it! :popcorn:

---

### Post by rparker on 2009-11-25
Hi,

I follow the steps through:
sudo apt-get build-dep mail-notification
sudo apt-get install libssl-dev fakeroot

and then:
cd mail-notification-4.1.dfsg.1

response was:
No such file or directory

Please help. Thank you.

---

### Post by mack75 on 2009-11-27
Hi:

You need to download the source code.

Do you has executed: apt-get source mail-notification ???

Don't move from the current directory, preferably in /tmp

After doing this, go to through missing steps

Regards

---

### Post by rparker on 2009-11-28
mack75,

Thank you for responding. Yes I had executed apt-get source mail-notification. I did notice though that a directory was not created within /tmp so I executed it again. Then I entered cd /tmp/mail-notification-5.4.dfsg.1 (notice the file name change). From there I followed the balance of the "How To" with success.

Thank you!

---

### Post by mack75 on 2009-11-30
Thanks rparker for the notice.

---

### Post by vip_n on 2009-12-01
Hi all,

Thanks a lot for this how-to but I'm struck with a bit of a problem ...

The package [COLOR=Blue]libgtkhtml-dev [COLOR=Black]just won't install (I'm on a 64-bit karmic)[/COLOR] [COLOR=Black]when I try to install it manually. It seems that I cannot get all its dependencies (especially libbonobo2_1 that needs itself to be installed ...).

Maybe there is a workaround ?
[/COLOR][/COLOR]

---

### Post by mack75 on 2009-12-01
Hi vip_n:

I don't have a PC to install 64 bits distro, but, can you copy to us the output from the apt-get install libgtkhtml......??

Can you try to install this packages?: sudo apt-get install gtkhtml3.8 libgtkhtml3.8-dev libgnomeprint2.2-dev libebook1.2-dev [COLOR="Red"]libgtkhtml2-dev[/COLOR] libgtkhtml-editor-dev

Notice that the package libgtkhtml-dev has been replaced for libgtkhtml2-dev

Good luck! and let us know the results.

Regards

---

### Post by vip_n on 2009-12-02
I installed [COLOR=Red]libgtkhtml2-dev [COLOR=Black]as the [/COLOR][/COLOR]libgtkhtml package could not be found with apt-get. 

Then I couldn't find mail-notification in /usr/bin/ but (after reading the compilation output) I realized that I had to install the package that has been created (in /tmp/). After installing it, it worked like a charm !

Thanks for the help, but I still don't know why the program doesn't install directly (as it did in 9.04 after recompile).

---

### Post by FuePi on 2009-12-08
Hi mack75, 

the guide worked very well :)

Thanks.

---

### Post by mack75 on 2009-12-08
Hi vip_n:

In reply to:

*"but I still don't know why the program doesn't install directly (as it did in 9.04 after recompile)."*

maybe because I forgot to tell you: first install the mail-notification packege and then execute this guide. :-)

Sorry.

Regards

---

### Post by Naaktgeboren on 2010-01-29
There is also a PPA with mail-notification packages built with SSL support:

[https://launchpad.net/~mail-notification-ssl/+archive/ppa](https://launchpad.net/~mail-notification-ssl/+archive/ppa)

---

