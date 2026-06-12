---
title: "ubuntu 10.4 LTS blank screen with cursor blinking after install"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by sandyu on 2010-06-04
I have installed today Ubuntu 10.4 LTS ..after installation the OS does not boot and just shows blank screen with cursor blinking ...any idea ..I have searched the forum a lot but cannot understand why this is happening ..re-installed twice ..

This is AMD64 bit but I am installing the 32 bit ubuntu 10.4 LTS. Please help ..otherwise I would have no choice but to go for Windows 7.

thanks
Sandy

---

### Post by davidmohammed on 2010-06-04
probably a graphics issues.

I've noticed quite a few black screen threads.  Worth searching...

similar thread [here]("http://ubuntuforums.org/showpost.php?p=9387310&postcount=7")

---

### Post by kansasnoob on 2010-06-04
> **sandyu said:**
> I have installed today Ubuntu 10.4 LTS ..after installation the OS does not boot and just shows blank screen with cursor blinking ...any idea ..I have searched the forum a lot but cannot understand why this is happening ..re-installed twice ..

This is AMD64 bit but I am installing the 32 bit ubuntu 10.4 LTS. Please help ..otherwise I would have no choice but to go for Windows 7.

thanks
Sandy

Is that the only OS on that machine?

I'm just curious if the boot menu appears or not?

If not try holding down the Shift key right after the System/BIOS screen passes, then select to boot into the recovery mode, after it completes you'll see a list of options, select failsafeX.

If that gets you a graphic we really need to see the output of the following to determine the exact graphics chip:

```
lspci | grep VGA
```

If no recovery mode is displayed in the boot menu:

> How to Boot to the Recovery Mode w/o a Menu Option

   1. If you have Grub 2 set to boot without displaying the menu at all, hold the SHIFT key down until the menu displays. (In Grub it was the ESC key.)
   2. Press any key once the menu is displayed to 'freeze' it. Then arrow to the kernel you want to boot.
   3. Press "e"
   4. Scroll to the end of the "linux /boot/vmlinuz...." line. If displayed, remove "quiet" and/or "splash". Add the word "single" to the end of the line.
   5. Press CTRL-X to boot to the Recovery menu.


Shamelessly stolen from:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2010-06-04
Just for fun:

> otherwise I would have no choice but to go for Windows 7.

With so many distros to choose from:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Master001 on 2010-06-04
Every distro I tried died on my machine, whether it was a 64 bit for amd or 32 bit for amd/ibm... 
 
I get the same thing except for 1 os, the Mint9 for AMD  its the only one that would allow me to boot and at that it was only the live CD
 
My box, AMD 64 Phenom quad core, and 7 gig ram, 2 BFG 9800GTXOC2's SLI config
 
now my q is why cant I get this to install UBUNTU 10.4 AMD64/Server, it says install but then fails to give me a GUI, I get command line only then it asks for Admin password, I supply the one used during install and it fails.. then endless loop..
 
Forgive me, I am noob to this Linux but wanted to dive right into the Server as i want to make the jump from M$ into linux and get away from the problems of Virus and spyware on MY M$ Exchange Server/ Web server...
 
Thanks ahead.
Bill

---

### Post by davidmohammed on 2010-06-04
> **Master001 said:**
> Every distro I tried died on my machine, whether it was a 64 bit for amd or 32 bit for amd/ibm... 
 
I get the same thing except for 1 os, the Mint9 for AMD  its the only one that would allow me to boot and at that it was only the live CD
 
My box, AMD 64 Phenom quad core, and 7 gig ram, 2 BFG 9800GTXOC2's SLI config
 
now my q is why cant I get this to install UBUNTU 10.4 AMD64/Server, it says install but then fails to give me a GUI, I get command line only then it asks for Admin password, I supply the one used during install and it fails.. then endless loop..
 
Forgive me, I am noob to this Linux but wanted to dive right into the Server as i want to make the jump from M$ into linux and get away from the problems of Virus and spyware on MY M$ Exchange Server/ Web server...
 
Thanks ahead.
Bill


If you are installing the server version - it doesn't come with a gui - you need to install the gdm_desktop if you want the gui.

When you say you enter the admin password, fails and endless loop - what sort of loop?  Does it reboot, or just goes back to asking for your username and password?

---

### Post by Master001 on 2010-06-04
> **davidmohammed said:**
> If you are installing the server version - it doesn't come with a gui - you need to install the gdm_desktop if you want the gui.
 
When you say you enter the admin password, fails and endless loop - what sort of loop? Does it reboot, or just goes back to asking for your username and password?
 
It just keeps prompting for a user id and password saying it fails to authenticate..
 
What is the command structure to install the GUI.,
Thanks
Bill
 
Is it something like 
sudo apt-get install gdm_desktop  ?

---

### Post by sandyu on 2010-06-07
Thanks for the response. For me nothing comes ..no login screen at all ..today I installed 10.4 LTS 64bit as this is an AMD 64bit machine ...same thing happens ..

The graphics shown as :

buntu@ubuntu:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
ubuntu@ubuntu:~$ 

any idea ? I really need to get this done as otherwise no option but have windows ..which I do not want to.

thanks
sandy

---

### Post by sandyu on 2010-06-07
yes this is the only OS on this machine ..I erased the /dev/sda and installed fresh ..also from live CD everything works perfectly ..that is how I am able to reply to this thread !

please help..

---

### Post by sandyu on 2010-06-07
I tried pressing SHIFT key during boot but nothing happens ..just the cursor blinks ..this is desktop edtion 64bit...any clue ?

---

