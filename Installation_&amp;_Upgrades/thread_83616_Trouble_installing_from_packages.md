---
title: "Trouble installing from packages"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by Zynga on 2005-10-29
When It's in the middle of installing(From the hd, by it's self) It hangs at a file called gstreamer0.8-jpeg   It stays there for a while and then a box comes up and says that there was a problem installing the selected software so it has me press ok and then it takes me to a box with some unusual characters and the box says Failed to start the X server (Your graphical interface).  It is likely that it is not set up correctly. Would you like to view the X Server otput to diagnose the problem?  so I press yes and it is just a gray box. with no writing in it.  Does anyone have any idea how I can fix this problem? I have tried twice and still it says the same thing.

---

### Post by Zynga on 2005-10-29
Hm... It seems no matter how many times I fully install Breeze it always has this X error when you start up.  Hm... I also get the error when I try to use the Live disk so the live disk doesn't work either >.>  Could it be a hardware problem?

---

### Post by RayH on 2005-10-29
I believe that's a basic multimedia plugin.  I did a quick search but didn't find anything similar to your error.  Have you run any other distributions before?  How is your disk space?  What is your hardware?

---

### Post by Zynga on 2005-10-29
[QUOTE=RayH]I believe that's a basic multimedia plugin.  I did a quick search but didn't find anything similar to your error.  Have you run any other distributions before?  How is your disk space?  What is your hardware?[/QUOTE]

No I havn't run any other distributions before. For many years I have stuck along side windows and have recently decided to switch.

I only have harddrive and it's an 80 gig that's partitioned
14.7GB (Windows)
41.9GB (Everythng from games to files  
20.0GB (Ubuntu)
3.4GB  (Swap Space)

Ok and my hardware
2.5ghz Intel Celeron
768mb Ram
80gb hard drive
GForce FX 5500 Verto Series(PCI)
DVD-RW drive
And it also runs windows

---

### Post by RayH on 2005-10-29
I'm no expert but I'm wondering if the video card is causing the problem.  Even though the install references the gstreamer file it's also trying to load the graphical interface which is where it also appears to be failing.  How did the PCI card come about in a 2.5ghz celeron?  Did you add it in afterwards?  Is there an integrated card?  If so I wonder if you'd be succesful by removing the PCI card and let it run off the integrated one.  I know it might not be ideal at first, but technically an AGP card would be much better for Windows and Linux.

If you're getting a bit discouraged don't worry yet.  There's a slight learning curve but Ubuntu is a great distro.  Once we get through this install issue there are some great programs to use (Automatix and Easy Ubuntu) that really make you wonder how long Windows will remain on top :cool:

---

### Post by Kyral on 2005-10-29
Try installing nvidia-glx with apt

```
sudo apt-get install nvidia-glx
```

and then 

```
sudo dpkg-reconfigure xserver-xorg
```

And select the "NVidia" module from the list ( I think its the first one)

---

### Post by Zynga on 2005-10-29
Ok, The Nvidia card was a one a while back becase I was quite unhappy with the integrated Intel Card.

I tried reinstalling for the fourth time, this time instead of deleting partitions, kept the same partitions and just reformatted them. I got better results this time. I managed to get all the way through the setup on the cd to the setup on the HD. And got through that. However the first boot of the hard drive I get the X is not set up properly blah blah blah.  But the screen after says something this time

```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523
root@vernadsky.buildd)
Release Date: 9 Febrary 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Crrent Operating System Linx Ubuntu 2.6.12-9-386 #1 Mon Oct 10
13:14:39 BST 2005 i686
Build Date: 10 October 2005
     Before Reporting problems, check http://wiki.x.Org
     To Make sure that you have the latest Version
Modle Loader Present
OS Kernal: Linux version 2.6.12-9-386 (Buildd@rothera)  (gcc version
3.4.5 20050809 (Prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10
13:14:36 BST 2005
Marker: (--) probed, (**) form config file, (==) default setting,
```

Hopefully this will help figure out what is wrong?

---

### Post by Zynga on 2005-10-29
Ok I got the Nvidia drivers installed into it's config, and when I get back to the evan@ubuntu:~$, I type in startx

It comes up with a 

[CODE]
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 29 15:46:00 2005
(==) Using config file: "/ect/X11/Xorg.conf
(WW) NVIDIA: No matching device section for instance (BusID PCI:2:9:0) found
(EE) No Devices detected

Fatal Server error:
No screens found


So how do you fix the no screens found error?

---

### Post by RayH on 2005-10-29
Plug and play enabled?  Maybe the bios assigned it resources different from where the OS is looking.  I still say that you should try removing the PCI card, you could always do the install and then follow graphics card upgrade instructions that are available here via search.

---

### Post by Zynga on 2005-10-29
Ok I followed the directions on x.org's site and redownloaded and reinstalled the nvidia drivers apparently the problem was that the device I tried to install the drivers for was not the right card, It was trying to install the nvidia drivers to the Intel Integrated Card, so once I reinstalled it with the drivers mapped the nvidia card, it worked just fine, thanks for your help guys

---

### Post by deepthought on 2005-11-01
Hello Zynga,

i have got the same installation Problem with gstreamer0.8-jpeg.
"Ok I followed the directions on x.org's site and redownloaded and reinstalled the nvidia drivers" 
-> I can not find the directions on x.org, can you give me a Link.
"so once I reinstalled it with the drivers mapped the nvidia card"
-> I didn't understand.
A short instruction would be helpful.

---

### Post by Abd-al-Karim on 2005-11-01
Hi I am  having similar problems as Zynga after I did a **sudo apt-get dist-upgrade** on Hoary. The install went fine (or so i thought), but then the machine boots (its an i386  BTW with a Windows partition first and then Ubuntu on that, a pretty standard install just a root and a swap partition) and just like Zynga X won't start but I get a load of other erros too.

I chronological order my errors go like this:
```
locale : Cannot set LC_CTYPE to default locale: No such file or directory
locale : Cannot set LC_MESSAGES to default locale: No such file or directory
locale : Cannot set LC_ALL to default locale: No such file or directory
null symbol found
```
then after setting up the general console font is successful I get the above error again.

Then although network setting are succesfully configured 
I get a: ```
*Synchronising clock to ntp.ubuntulinux.org [fail]
```
followed by: ```
*ror: Tempoary failure in name resolution
```
[for some reason Internet is not working even though it works fine on other machines using the same conncection I have tried pinging sites and lynx to no avail I can also not ping my default gateway (ethernet router)]
Then: ```
*Starting the Firestarter firewall: sit0: error fetching interface information
 sit0: error fetching device information not found [fail]
 sit0: error fetching device information not found [fail]
 failed.
```
And:
          ```
*Starting deffered execution scheduler. [fail]
```
then I get the same dialog as Zynga described namely:
Blue background gray text box: ```
I cannot start the X Server (graphical interface). It is likely that it is not 
setup correctly. Would you like to view the X server output to diagnose the problem?
<Yes> <No>
```
Then I just get a big blank gray box and "<Ok>" which after pressing enter give another gray box saying: ```
I will disable X for now. Restart GDM when it is configured properly <Ok>
```
I have tried a number of things including:

**sudo dpkg-reconfigure xserver-xorg**

but that gives:
```
perl: warning: Setting locale failed
perl: warning: Please check that your locale settings:
             LANGUAGE = "en_ZA:en",
             LC_ALL = (unset)
             "LANG = "en_ZA.UTF-8"
      are supported on your system 
perl: warning: Falling back to the standard locale ("C").

locale : Cannot set LC_CTYPE to default locale: No such file or directory
locale : Cannot set LC_MESSAGES to default locale: No such file or directory
locale : Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.
```

I suppose I could force to reconfigure using **sudo dpkg-reconfigure -f xserver-xorg**, right? but I don't wanna do that just yet I might really break my system. 

I have also tried to resolve package conflicts by using **sudo apt-get -f upgrade** but that will remove 257 packages (753Mb) including important ones like ubuntu-base, ubuntu-desktop, x-window-system-core and others. Since I don't have Internet on that machine at the moment I don't want to do that just yet either.

Thanks a lot, if any one has any ideas that could help me then that would be greatly appreciated.

**PS:** I almost forgot what i also find strange is that Grub tells me that I still have a 2.6.10 kernel (when I login it tells me that also) even though breezy should have a 2.6.12? More strange is that fact that I have logged in on this machine a couple of times and although it gives a completely wrong date when I log in (and a time thats a few minutes off *I think*) it always displays the correct date and time for the last time I logged in :confused:.

---

### Post by Abd-al-Karim on 2005-11-01
I thought I might just add that I also tried **sudo dpkg-reconfigure locales** but that gave me the same results as **sudo dpkg-reconfigure xserver-xorg**. I have searched the wiki and forums but found nothing that could help. Though another person submitted this as a bug [here]("https://bugzilla.ubuntu.com/show_bug.cgi?id=13264#add_comment") and I added my story there too.

---

### Post by Abd-al-Karim on 2005-11-03
I just wanted to bump this up and ask for some suggestions please.

---

