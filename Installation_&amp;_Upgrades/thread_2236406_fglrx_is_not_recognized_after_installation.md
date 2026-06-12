---
title: "fglrx is not recognized after installation"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by jan-banan on 2014-07-26
I've had fglrx with no problem since I installed 14.04 when it came out, and today I started troubleshooting some hardware stuff so I had to remove my graphics card, a Radeon R9 280X. All was fine and dandy, I rebooted, did my things and then mounted the graphics card again. I didn't notice any issues until I played some Minecraft and realized that the fan was spinning, which it shouldn't since I run the game with V-sync, so I whent to check out amd control center but I could'nt find it. 

I started looking around to verify that everyhing was as it should be and realized that everyhing was installed but Ubuntu didn't recognize that fglrx was installed. So I tried reinstalling the driver after purging it first, it installed with no hickups but when I tried to enter "sudo aticonfig --initial" it says that it cannot find the command. I purged the driver again and tried fglrx-updates to no avail, then I tried installing the may-release found in the driver installer that is provided by the Fanclub (great tool btw, just klick next, pick your version and then you're basically done!) but still no go. 

When I go to the GUI-installer for proprietary software it shows that the proprietary driver is in use, but when I check out "Details" in the settings panel the overview shows that I am using the open source driver. fglrxinfo isn't found, aticonfig isn't found, amdconfig isn't found and fglrx-amdcccle isn't found but everything is installed. How can I troubleshoot this further and fix the issue?

EDIT, instructions on how to attempt to fix the issue:
I have condensed the commands that I believe were the ones that I needed to run in order to fix the issue. I want to give credit to this thread for giving me the final clues [http://askubuntu.com/questions/445954/unable-to-open-etc-ati-control-please-reinstall-the-driver](http://askubuntu.com/questions/445954/unable-to-open-etc-ati-control-please-reinstall-the-driver) and also slooksterpsv for bouncing ideas with me. I really didn't want to reinstall Ubuntu and thankfully I didn't need to.

If you have run into the same problem, I would advice you to run the following commands before you proceed with symlinking as shown below.
```
sudo apt-get purge fglrx fglrx-amdcccle
sudo apt-get clean
sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle
```

This is in order to make sure that you begin with a clean sheet in case any previous changes cause the following commands to not work. If you prefer the drivers found on AMD's website then go ahead and use them, but I do not know if this fix will work since I used the official driver from Ubuntus respositories. Although there shouldn't be any difference.

Run the following commands in a terminal. The third line has two commands on it, if the first one doesn't work after a reboot, then try the second one.
```
sudo ln -s /usr/lib/fglrx/bin/aticonfig /usr/bin/aticonfig
sudo ln -s /usr/lib/fglrx/etc/ati/ /etc/ati
sudo ln -s /usr/lib/fglrx/bin/amdcccle /usr/bin/amdcccle
sudo ln -s /usr/lib/fglrx/bin/fglrxinfo /usr/bin/fglrxinfo
sudo /usr/lib/fglrx/switchlibGL amd # or sudo /usr/lib/fglrx/switchlibglx amd
```
reboot
```
sudo aticonfig --initial
```

Verify that the driver is now working by running the following command in a terminal.
```
fglrxinfo
```
If you get an output similar to this
```
jan@Hyper:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: **AMD Radeon R9 200 Series**                          
OpenGL version string: **4.3.12798 Compatibility Profile Context 13.35.1005**

```
as opposed to
```
jan@Hyper:~$ sudo fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: X.Org
OpenGL renderer string: **Gallium 0.4** on AMD TAHITI
OpenGL version string: **3.0 Mesa 10.1.3**
```
Then it was successful. 
If not, write a comment with the output from the commands shown above.

---

### Post by slooksterpsv on 2014-07-26
Run the following commands:

```

sudo updatedb
sudo locate aticonfig

```

If that doesn't return anything, then it's not installed - which would tell me its actually using an opensource driver and not one provided by AMD.

---

### Post by jan-banan on 2014-07-27
This is the output from the commands listed above.
```
jan@Hyper:~$ sudo updatedb
[sudo] password for jan: 
jan@Hyper:~$ sudo locate aticonfig
/etc/acpi/events/fglrx-ac-aticonfig
/etc/acpi/events/fglrx-lid-aticonfig
/home/jan/Downloads/amd-catalyst-14-4-rev2-linux-x86-x86-64-may6/fglrx-14.10.1006.1001/doc/examples/etc/acpi/events/a-ac-aticonfig
/home/jan/Downloads/amd-catalyst-14-4-rev2-linux-x86-x86-64-may6/fglrx-14.10.1006.1001/doc/examples/etc/acpi/events/a-lid-aticonfig
/usr/lib/fglrx/bin/aticonfig
/usr/share/doc/fglrx/examples/etc/acpi/events/a-ac-aticonfig
/usr/share/doc/fglrx/examples/etc/acpi/events/a-lid-aticonfig
```

---

### Post by slooksterpsv on 2014-07-27
Odd... it should be in /usr/bin. What about downloading the run file from AMD? I'd try that, my fglrx-updates installed properly - hmm....

---

### Post by jan-banan on 2014-07-27
I purged the already installed driver, downloaded the 14.4 version of the driver and installed it with no complaints coming from the terminal. The I tried running sudo aticonfig --initial but the command wasn't found, I ran sudo updatedb and sudo locate aticonfig but the binary wasn't in /usr/bin as you said it should be. 
So I tried the latest beta version but nothing changed, everything installed correctly but I cant execute fglrxinfo, aticonfig or amdcccle. I even rebooted but it didn't change anything. It still says in the proprietary drivers window that I am using the proprietary driver, but the Details window in the settings panel shows that I am using the open source gallium driver. It's pretty baffling since it all works as far as I can tell, everything installs but in the end the driver isn't working? :confused:

---

### Post by jan-banan on 2014-07-27
So I have tried some more stuff. First of all I tried to run the binaries directly, but it returned that it couldn't find any supported adapters. So I googled that and found out that several other people had had the same problem, one guy fixed it by symlinking the binaries from /usr/lib/fglrx/bin/ to /usr/bin but that didn't do it for me, it still couldn't find a supported adapter. So I read some more and saw that I hadn't installed ia32-libs as required by the tutorial because... it doesn't exist in the trusty repositories. I found this emergency hack that allowed me to install ia32-libs:

```
sudo apt-get install libc6:i386
sudo -i
cd /etc/apt/sources.list.d
echo "deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse" >ia32-libs-raring.list
apt-get update
apt-get install ia32-libs
rm /etc/apt/sources.list.d/ia32-libs-raring.list
apt-get update
exit
sudo apt-get install gcc-multilib
```

bit I still couldn't install the driver and have aticonfig etc end up in /usr/bin as it should, and neither could I run the binaries from where they are right now since it can't find a supported adapter. To be precise, this is the output:
```

jan@Hyper:~$ sudo /usr/lib/fglrx/bin/aticonfig
Unable to open /etc/ati/control, please reinstall the driver.
/usr/lib/fglrx/bin/aticonfig: No supported adapters detected
```
I checked out /etc/ati but it doesn't even exist. I tried to install the latest beta driver that has official support for 14.04 but still no success. Something is seriously messed up since so many things seem to go wrong. I found this bugreport too: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1304376](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1304376)
It looks like it isn't prioritized at the moment though, the bug report is almost 4 months old now and hasn't been assigned yet.

I really don't want to reinstall Ubuntu... :cry:

---

### Post by slooksterpsv on 2014-07-27
I wouldn't use older repositories, and the 32-bit shouldn't be required at all if you're running 64-bit. It should install both sets from fglrx, fglrx-updates, etc.

Have you purged the fglrx and also cleaned your downloads in case it was a bunk download from the repos? E.g.

sudo apt-get purge fglrx fglrx-amdcccle
sudo apt-get clean
sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle

---

### Post by jan-banan on 2014-07-28
Nope, purging, cleaning, updating and installing doesn't help =/

EDIT: I created symlinks from /usr/lib/fglrx/bin/ to /usr/bin for aticonfig, fglrxinfo, amdcccle and a symlink from /usr/lib/fglrx/etc/ati to /etc/ati and now I can run all of the symlinked binaries. Then I successfully ran aticonfig --initial, rebooted but it still didn't work properly. So I ran sudo aticonfig --initial again and got this output:
```
jan@Hyper:~$ sudo aticonfig --initial
[sudo] password for jan: 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original
```

Then I ran it again since the file was unitialised, strangely enough. The second time around I got this output:
```
jan@Hyper:~$ sudo aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx
```

Anyway, running fglrxinfo returns this:
```
jan@Hyper:~$ sudo fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD TAHITI
OpenGL version string: 3.0 Mesa 10.1.3
```

I tried running sudo amdcccle and got a popup window saying that there was a problem that might have been due to either that the driver isn't installed or that the driver isn't working as it is supposed to. Then it says I should install it or configure it using aticonfig.

I rebooted to see if the changes would stick but fglrxinfo still shows gallium as the current driver. So symlinking the missing binaries worked, but running aticonfig isn't effective.

EDIT2: I DID IT! OH MY GOD BABY JESUS SON OF MARY!!! I hope that the following is the only thing that was needed apart from all of the above, I want this thread to be as complete as possible in case someone else runs into the same issue. I finally ran "sudo /usr/lib/fglrx/switchlibGL amd" and rebooted and ran "sudo aticonfig --initial" and lo and behold, fglrxinfo returned this sweet output in my terminal:
```
jan@Hyper:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R9 200 Series                          
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005
```

Thank you slooksterpsv for your input, I needed someone to bounce ideas off of! ):P

---

