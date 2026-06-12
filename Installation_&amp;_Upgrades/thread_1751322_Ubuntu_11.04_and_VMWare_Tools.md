---
title: "Ubuntu 11.04 and VMWare Tools"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by onlymehere on 2011-05-06
I had hoped that Linux is getting easier to use.

Using VMWare 2.0.4, and when I go to "Install VMWare Tools", I get a window that has three files - manifest.txt, VMWareTools-7.7.6-203138.i386.rpm, and VMWareTools-7.7.6-203138.i386.tar.gz.

Why is it that I can't just click on a file and have it install?   I run a simple commandline to run setup.ncf for NetWare and it auto-installs.  For Windows, it's even easier.

How do I get this installed for Ubuntu v11.04?

Thank you.

---

### Post by Zerocool3001 on 2011-05-14
I'm a little surprised no one has replied to you. I haven't run vmware on a windows machine, but the process for installing vmware tools should be the same. You should un tar the tar.gz file (you can do this in the command line or simple double click in gnome usually brings up the archive manager). Then open a new terminal and navigate to the extracted directory. Once there, you should see something like "install-vmware-tools.pl". Run this with root permissions and it should guide you through the installation process.

Hope that helps.


Additionally, you can use the open source version of vmware tools. It is available in the repositories and can be installed from the software center, synaptic, or any other package manager.

---

### Post by azsunlove79 on 2011-05-18
I've just installed 11.04 and I'm running it in a VM.  I go to install VMware Tools and I get a "Unable to Install VMware Tools:  Not Authorized"  Does anyone have any idea what that is all about?  Yesterday I was able to send the VMware Tools install from vCenter and it mounted under /media but today I can't get it installed.  I would appreciate any help I can get.  

-Greg

---

### Post by azsunlove79 on 2011-05-18
You should open a terminal and go to the directory where your VMware Tools install file is mounted and then run this command:

dpkg -i <your VMware Tools file>  

It should be the tar file, since you can't use the RPM in Ubuntu.  

Does that help??

---

### Post by Zerocool3001 on 2011-05-19
> **azsunlove79 said:**
> I've just installed 11.04 and I'm running it in a VM.  I go to install VMware Tools and I get a "Unable to Install VMware Tools:  Not Authorized"  Does anyone have any idea what that is all about?  Yesterday I was able to send the VMware Tools install from vCenter and it mounted under /media but today I can't get it installed.

What problem are you having exactly? Is it that you can't mount the vmware tools cd inside the VM? Or can you not install the tools once they are mounted? Again, I'm less familiar with VMware on windows machines, but the process should be similar.

---

### Post by Dennis M on 2011-09-02
I just installed 11.x on VMWare 7...

However, when I boot it, it comes up and comes up with a message indicating it wants to install VMTools, and asks for login... I login and it goes to a command line... Several Tutorials I found, do not work...

[IMG]http://img820.imageshack.us/img820/305/ubuntu11.png[/IMG]


After I login, it just sits there... I have restarted the system multiple times trying to just get to the GUI and selected 'Cancel VMTools Installation' from the Tools menu of VMWare before booting...

Any ideas?

---

### Post by Zerocool3001 on 2011-09-05
I'm not very familiar with the Windows version of VMWare, but you might try skipping the Easy Install when it asks for your username and password. Then you can use the manual install once you're logged in.

---

### Post by Joshua49 on 2012-04-17
Hi, 
I remember the "easy install", but not what happened from it. My VM Player just told me there is a new version of the tools available, so I did - this is the process how it worked : 

Make sure following are installed : 
* gcc compiler
* make
* binutils
* kernel header files (execute "uname -r" to get the version of the kernel running)

With Ubuntu 11.04, use following paths : 
[LIST]
[*]gcc : /usr/bin/gcc
[*]/usr/bin/make
[*]/usr/src/linuc-kernel-header-<versionnr>/include
[/LIST]


Either go here : 
 [http://ubuntuforums.org/showthread.php?t=1561822]("http://ubuntuforums.org/showthread.php?t=1561822")
or : 
1) Push "Install" or choose "Virtual Machine -> install VMwre tools" in the menu
2) Push the Help button for detailed steps : 
> Manually Install or Upgrade VMware Tools in a Linux Virtual Machine
For Linux virtual machines, you manually install or upgrade VMware Tools by using the command line.
Install the latest version of VMware Tools to enhance the performance of the virtual machine's guest operating system and improve virtual machine management. When you power on a virtual machine, if a new version of VMware Tools is available, you see a notification in the status bar of the guest operating system.
Prerequisites
&#9632;  Power on the virtual machine. 

&#9632;  Verify that the guest operating system is running. 

&#9632;  Because the VMware Tools installer is written in Perl, verify that Perl is installed in the guest operating system. 

Procedure
1  On the host, from the Player menu bar, select Virtual Machine > Install VMware Tools. 

If an earlier version of VMware Tools is installed, the menu item is Update VMware Tools.
2  In the virtual machine, log in to the guest operating system as root and open a terminal window. 

3  Run the mount command with no arguments to determine whether your Linux distribution automatically mounted the VMware Tools virtual CD-ROM image. 

If the CD-ROM device is mounted, the CD-ROM device and its mount point are listed as something like this:
/dev/cdrom on /mnt/cdrom type iso9660 (ro,nosuid,nodev)4  If the VMware Tools virtual CD-ROM image is not mounted, mount the CD-ROM drive. 

a  If a mount point directory does not already exist, create it. 

mkdir /mnt/cdromSome Linux distributions use different mount point names. For example, on some distributions the mount point is /media/VMware Tools rather than /mnt/cdrom. Modify the command to reflect the conventions that your distribution uses.
b  Mount the CD-ROM drive. 

mount /dev/cdrom /mnt/cdromSome Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, modify the command to reflect the conventions that your distribution uses.
5  Change to a working directory (for example, /tmp). 

cd /tmp
6  Delete any previous vmware-tools-distrib directory before you install VMware Tools. 

The location of this directory depends on where you placed it during the previous installation. Often this directory is placed in /tmp/vmware-tools-distrib.
7  List the contents of the mount point directory and note the filename of the VMware Tools tar installer. 

ls mount-point8  Uncompress the installer. 

tar zxpf /mnt/cdrom/VMwareTools-x.x.x-yyyy.tar.gzThe value x.x.x is the product version number, and yyyy is the build number of the product release.
If you attempt to install a tar installation over an RPM installation, or the reverse, the installer detects the previous installation and must convert the installer database format before continuing.
9  If necessary, unmount the CD-ROM image. 

umount /dev/cdrom If your Linux distribution automatically mounted the CD-ROM, you do not need to unmount the image.
10  Run the installer and configure VMware Tools. 

cd vmware-tools-distrib./vmware-install.plUsually, the vmware-config-tools.pl configuration file runs after the installer file finishes running.
11  Respond to the prompts by pressing Enter to accept the default values, if appropriate for your configuration. 

12  Follow the instructions at the end of the script. 

Depending on the features you use, these instructions can include restarting the X session, restarting networking, logging in again, and starting the VMware User process. You can alternatively reboot the guest operating system to accomplish all these tasks.

---

