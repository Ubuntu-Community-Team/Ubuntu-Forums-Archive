---
title: "Installing 10.10 - User ubuntu not found"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2010-10-11
My experiences installing 10.10 yesterday:

1. Booting up from a LiveCD on my desktop gives me a login screen but no way to log in. When I hit <escape> during the bootup, I see the message the the user "ubuntu" doesn't exist. So there is no way to continue with the installation. I can't even switch to a console. Also can't restart or shutdown from the login screen. Have to pull the power cord. Maybe this CD is bad? I wanted to install via Alt CD anyway...

2. Alternate CD: everything goes fine until 73% of the way through installing the base system, when the installer hangs. It will not go any further. [I think this is an old unsolved bug]("http://ubuntuforums.org/showthread.php?t=1108652").

3. USB Stick made from Alt CD ISO: Linux Mint 9 fails to make a USB startup disk for unknown reasons, so I boot into Jaunty and make a USB startup disk from the Ubuntu 10.10 iso. Boot my computer with this and the bootup fails with [error "unknown keyword in script"]("http://ubuntuforums.org/showthread.php?p=9948980").

All-in-all, a full day of effort without being able to successfully install Ubuntu. Still don't have it installed.

---

### Post by MountainX on 2010-10-11
Day Two: finally got it installed. Had to burn another LiveCD. Alternate CD won't get past 73%... Using LiveCD prevents me from partitioning the way I want to, but at least it is installed now.

---

### Post by 2rB on 2010-10-14
I have the same problem as you with the Ubuntu 10.10 Alternate i386 installation CD.

"Installing the base system" is stuck at 73% displaying "Updating the list of available packages...".

---

I also have a problem installing from the Live CD. My problem is that I'm given an error telling me that I'm not able to install the boot loader.
(cant see that this is releated to your problem, so ignore this in this thread)

---

### Post by MountainX on 2010-10-14
The "stuck at 73%" error is a bug related to some specific hardware. I do not know the details, but I know I can install from the same CD on another computer and I do not get the error. So there is something about this specific hardware. The problem started around Ubuntu 9.04 and continues through 10.10. (I have also seen it get stuck at e.g., 74%, but it is always around this %).

My only solution is to install via USB or use a LiveCD.

---

### Post by 2rB on 2010-10-14
Got my installation to work now after trying again from the Live i386 CD.

The only difference this time vs. the other 3 times i tried installing from the Live CD is that this time I had installed two new HDD and moved two of the existing ones (not the one I installed the OS / boot loader to) to new SATA-ports on the motherboard.

Strange - but right now I'm just happy it works.

Thanks for information regarding the Alternate CD / ways around.

---

### Post by Dihi Doctor on 2010-10-27
I also had the same problem with the 10.10 alternative install CD - the installer was hanging at 73% (updating the list of available packages ...).

It may sound obvious, but the way I worked-around it was to physically disconnect my computer from the network before running the installer. This allows the installation to proceed without a problem, although you will obviously lose-out on any auto updates or network config that the installer would otherwise do (the installer did complain about no DHCP server being available ;))

This allowed me to install 10.10 using the partitioning scheme I wanted (LVM on software raid).

---

### Post by MadsR on 2010-11-05
I have the same issue on a "standard equipped" core i7 machine with nothing but mainstream components. System has previously installed and run Ubuntu 9.04 and 10.04 without any problems.

Trying to install 64bit Ubuntu 10.10 server. I am stuck at 73%. I have defined RAID0 in the BIOS but also tried without this. Using English installation but I select Danish keyboard.

Any help would be appreciated a lot! It seems (from Google) that quite a few users experience this issue.

Thanks,
Mads

---

### Post by MountainX on 2010-11-05
> **MadsR said:**
> I have the same issue on a "standard equipped" core i7 machine with nothing but mainstream components. System has previously installed and run Ubuntu 9.04 and 10.04 without any problems.

Trying to install 64bit Ubuntu 10.10 server. I am stuck at 73%. I have defined RAID0 in the BIOS but also tried without this. Using English installation but I select Danish keyboard.

Any help would be appreciated a lot! It seems (from Google) that quite a few users experience this issue.

Thanks,
Mads

The only solution I found was to install via a USB stick. However, you should read Dihi Doctor's post right above yours. Did you try that?

---

### Post by MadsR on 2010-11-05
MountainX - thanks for your answer - unplugging the ethernet? Yes I did without any luck. The server has WIFI maybe I should try to pull that card out? It's really weird that so many people have issues with this.

Anyways I just downloaded Ubuntu server 64 10.04 and it got another problem: "Please insert the disc labeled Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release (xxxxx". OMG this is so bad.

I must say that I have never observed such unstable installations in my long career of using and installing Linuxes. Even old FreeBSDs installs easier. Since I have been running all versions of Ubuntu since 8.04 on the machine I am pretty sure that there is nothing strange with the hardware.

This is sad, I was trying to test this server version for Ubuntu before we were going to install it on my companys HPC cluster next week. I am not sure I am going for the Ubuntu Server after seeing this. 

Last resort is USB, I am going to try that.
/Mads

---

### Post by MountainX on 2010-11-05
If it makes you feel any better, I must say that after I finally got Ubuntu 10.10 to install, it has been my best experience with Linux yet. I cannot express how much better Maverick is than any other distro/release I have tried yet. Of course, it is not perfect. But I am very, very happy with it after getting over the initial hurdles.

---

### Post by jarofgreen on 2010-11-05
I am also having hanging at 73% problems: neither removing the network or USB install worked for me :-( [http://ubuntuforums.org/showthread.php?p=10078309](http://ubuntuforums.org/showthread.php?p=10078309)

---

### Post by R33D3M33R on 2010-12-17
The alternate installer is useless for about two years now. First the media change problem, then this. It happens on certain hardware combinations (PATA disk and CD/DVD). The bad thing is - nobody cares about these fatal bugs and they will probably never get fixed:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/270461](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/270461)
[https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618](https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/316618)
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/364837](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/364837)
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/289702](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/289702)
[https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/274396](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/274396)

---

### Post by Veyasu on 2011-02-02
Hello!

I am going to use Ubuntu to teach systems administration at a college university starting next week, and I ran into the 73% hang problem on our lab computers. After 5 hours today, which I was going to use to prepare the first lesson, I was quite frustrated by this problem.

However, there is a really, really easy solution to this.

Before going through with partitioning, press Alt+F2 and press enter to activate the console. Then you type in "ln -s /cdrom /media/cdrom". Press Alt+F1 to get back and keep going as usual, and it works!

I figured this out by pressing Alt+F4, which is the console where the installer spews out a lot of information about what it is doing, and it is looking for the packages in /media/cdrom, while it mounts the cdrom at /cdrom. So by creating a symlink it finds the files it is looking for and thats it. :D

---

### Post by MountainX on 2011-02-02
> **Veyasu said:**
> Hello!

I am going to use Ubuntu to teach systems administration at a college university starting next week, and I ran into the 73% hang problem on our lab computers. After 5 hours today, which I was going to use to prepare the first lesson, I was quite frustrated by this problem.

However, there is a really, really easy solution to this.

Before going through with partitioning, press Alt+F2 and press enter to activate the console. Then you type in "ln -s /cdrom /media/cdrom". Press Alt+F1 to get back and keep going as usual, and it works!

I figured this out by pressing Alt+F4, which is the console where the installer spews out a lot of information about what it is doing, and it is looking for the packages in /media/cdrom, while it mounts the cdrom at /cdrom. So by creating a symlink it finds the files it is looking for and thats it. :D

Thanks! It's great to know the solution finally! I'll mark this thread as solved now.

But it would still be nice for Ubuntu to fix this issue. In fact, they could fix it with your solution because having that symlink in place would do no harm even in situations where it isn't needed.

---

### Post by DiagonalArg on 2011-02-12
Ok, that didn't solve the problem for me.  I was able to get beyond the 73% point, but I had to copy the four files:

/cdrom/dists/maverick/main/binary-i386/Packages.gz
/cdrom/dists/maverick/main/debian-installer/binary-i386/Packages.gz
/cdrom/dists/maverick/restricted/binary-i386/Packages.gz
/cdrom/dists/maverick/restricted/debian-installer/binary-i386/Packages.gz

under /media.  The soft link was not sufficient.  (in /media, "ln -s /cdrom .")

Unfortunately, copying didn't solve the problem either.  Later in the install, during "Select and Install Software", it got stuck at 14% (while it was reading 2000 some files).  Alt-F4 showed all kinds of hashsum errors, even though the CD is fine.  

I have now replaced my CD/DVD-RW (NEC) with a CD-RW and things are going swimmingly.  The problem appears to be (is in my case) that ubuntu is unable to handle the CD/DVD.  Someone else is reporting a problem with NEC CD/DVD's.  So I'm guessing this means a driver problem?

I'm going to wait for a few more mins before posting this, to make sure the install completes, but it does look fine....

Yup, all's good!

---

### Post by fluxxball on 2011-02-22
check out: [http://ubuntuforums.org/showthread.php?t=1685465](http://ubuntuforums.org/showthread.php?t=1685465)

after i attempted to install once:
1. boot in recovery mode
2. start shell in your new machines /root dir
3. ln -s /cdrom /media/cdrom
4. ctrl-D to bring up menu
5. select Go Back
6. select Install Base system

---

