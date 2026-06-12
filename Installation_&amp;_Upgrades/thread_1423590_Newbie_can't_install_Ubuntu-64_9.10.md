---
title: "Newbie can't install Ubuntu-64 9.10"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by dtset on 2010-03-06
I'm attempting to install the 64 bit version of Ubuntu 9.10 on my backup computer, a dual boot with Vista. I can get the initial screen, but I get an error when I try to check the disc for defects. I get a similar error when I try Live-CD (try Ubuntu without changing computer).

**Details, troubleshooting and a process of elimination:**

My backup computer was purchased on Craigslist a couple of years ago: it was home-built with an AMD Athlon-64 Dual Core Processor 3800+. Belarc Adviser assures me that it is 64-bit ready. It has Vista-32 installed on it. Last month I successfully installed Open-Suse 11.2 64 on it, so I know that it can run *some* version of 64 bit Linux. My machine also handles the 32 bit version of Ubuntu 9.10, at least in LiveCD mode. (Later, when I installed Win2000 over it, Opensuse 64 ceased to work. I then reconsidered my options and decided to work with the Ubuntu community. Greetings! I have since removed Win2000 and have Vista installed, along with a dead copy of Opensuse on a couple of Linux partitions.)

The 64 bit CD does not appear to be defective: it operates in Live-CD mode with my Dell Phenom X4.

Error for checking the disc:
I get a page of stuff ending with this line:

2.147161] [f gobbltygook ] child_rip +0x0/0x20

Error for Live CD 64 bit:
I get a page of stuff ending with this line:

2.147355] [f gobbltygook ] child_rip +0x0/0x20

"gobbltygook" is a string beginning in "f" that I didn't write down. Let me know if it would help.

Is the 64 bit version flaky?


**Ookay, what are my options?**

I could be directed to a thread/webpage on this topic which I have somehow missed.

I could think about trying the alternative install CD.

I could try an older version of the 64 bit Ubuntu.

I could try something else.

I could just install the 32 bit version. Maybe I could attempt a multiboot later.

I am an intermediate user in Windows who is brand spanking new to Linux. Any advice is appreciated, as my linux intuition is wholly undeveloped. I'd like to try some scientific software, which may or may not have improved performance with 64 bit.

(Am I correct in believing that I can run 32 bit linux programs with a 64 bit linux OS, albeit with some performance compromise?)

---

### Post by ptn107 on 2010-03-06
You should verify the .iso you have was not corrupted from the start.  From a terminal run:
```
md5sum *filename*
```
where *filename* is the target .iso file.  The result of that command is a 128-bit hash.  Verify that the hash of the image you downloaded matches the appropriate one from this list[1,2] _before_ you burn it to cd (always burn at the slowest speed possible).  After the hash is verified you can then boot the CD and select 'Check disk for defects'.

```
836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
74cfd79298e415c59ae0fee94ce97e47 *ubuntu-9.10-dvd-amd64.iso
cc61a62c08d6be87e561c15c5b9d6c1d *ubuntu-9.10-dvd-i386.iso

```

[1][http://releases.ubuntu.com/karmic/MD5SUMS]("http://releases.ubuntu.com/karmic/MD5SUMS")
[2][http://cdimage.ubuntu.com/releases/9.10/release/MD5SUMS]("http://cdimage.ubuntu.com/releases/9.10/release/MD5SUMS")

---

### Post by akand074 on 2010-03-06
Yeah I would just try burning a new cd first and make sure to verify the disk after burning. You can also try installing it without booting into the live cd first and see if the installation starts successfully.

---

### Post by dtset on 2010-03-06
The CD appeared to be fine.

I tested the MD5 hash with MD5 File and Folder Comparator Lite, a program I downloaded at PC world.  It matched.  I burnt a new CD.  It had the same symptoms (far right column of error message appeared identical).  Plus, the 64 bit Ubuntu Live-CD worked fine on my main computer, as I alluded to in my original post.  

Thanks for the help.  I still can't get the 64 bit Ubuntu Live-CD to work on my backup machine.  I'm inclined to wait until tomorrow before trying a direct install of the program.  If anybody has any other suggestions, I'd be much appreciative.

---

### Post by dtset on 2010-03-07
Ok I discovered F6, conveniently located at the bottom of the intro screen.  [Here is the Ubuntu help page dedicated to Boot Options]("https://help.ubuntu.com/community/BootOptions").  I can get the 64 bit Live CD to work, provided I choose, "acpi=off", which disables the [Advanced Configuration and Power Interface]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface").  

As I understand it, my options are:

[LIST]
[*]Install Ubuntu 9.10 - 64 with ACPI disabled
[*]Try another version of Ubuntu - 64 (8.04 LTS?)
[*]Install Ubuntu 9.10 - 32 -- this worked without editing in F6
[*]Try another distro of Linux 64 bit.
[*]Anything else?
[/LIST]
Will I get in trouble if I install Ubuntu64 9.10 with ACPI disabled?  Should I anticipate certain issues?  Advice and thoughts, above and below, are welcome and appreciated.

---

### Post by dtset on 2010-03-12
Problem resolved: Ubuntu 9.10 64-bit is now installed with the acpi=off option.  How do I change the forum tag?  

**Maybe someone will find this helpful**
This noob had to struggle with things for a while.  I wanted to dual-boot with Vista installed first.  When I tried to follow [this documentation page]("https://help.ubuntu.com/community/WindowsDualBoot"), I couldn't seem to find either something like "Resize IDE1 master, partition #1 (hda1) and use freed space" under "Automatic partition resizing", nor could I find "Size" under "Manually edit partition table".  I'm not saying that the Ubuntu instructions can't be made to work, only that I didn't have any luck with them.  

I ended up creating a new partition in Vista [using these instructions]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm"), and the helpful guide "[               Working Around Windows Vista's "Shrink Volume" Inadequacy Problems]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")".  A 15 day trial for Perfect Disk was also used.   

Once I had a 14GB FAT32 partition, I booted up the Live-CD (with the F6 option: acpi=off)  and attempted an install from within Linux.  Specify English, the time zone, the keyboard.  

Then choose the manual option for partitions.  Select my new (empty) partition, click the "Change..." button, edit the partition: set the size to 2000MB and choose "swap" from the dialog box list.  Click and wait.

I get a new entry: sda3.  Specify ext4 (what the heck), "primary", and for the mount point choose the lonesome forward slash.  I understand that's the root directory which is different than the /root directory.  Oh yeah, and everything is a file, whatever that means.  (Told ya I was a noob: you have been warned. :) )

Forward! 

Reboot and when grub2 delivers the boot up options, hit "e".  That will allow you to edit the grub2 command *for that time only*.  There will be an entry "quiet splash".  Change that to "quiet splash acpi=off".  Now hit CTRL-x and hopefully you can boot into ubuntu.  

If you don't want to do that rigmarole every time (and who does?) you will have to edit the grub2 menu.  grub2 is the latest and greatest version of grub and is now installed by default in Ubuntu.  Some documentation is here: [http://rhnotebook.wordpress.com/2010/02/14/grub-2-guide/](http://rhnotebook.wordpress.com/2010/02/14/grub-2-guide/)  Find the acpi=off reference.  

 If you're a recovering windows user, this may be your first introduction to linux users rights.  Apparently linux let's you run programs as an administrator *within* your session.  If you don't do all this, ubuntu will deny you permission to edit the relevant file.  Bummer.  

Hit ALT-F2 to get a command line.  
Enter the command "gksudo nautilus", with no quotes.

gksudo is a lot like "sudo".  "sudo" means "Run this program "from the root" with administrator privileges".  Or not.  "nautilus" is the file manager: they call it windows explorer or my computer in MS-land.  

From nautilus, press "File System" and make your way to -> etc/default/grub.  Right click the grub file, copy it, then paste it back into the directory.  Now you have a copy of the file.  Right click the grub file again and "Open with gedit".  

Now we tamper with the batch file.  Replace "quiet splash" with "quiet splash acpi=off".  Save the file and close gedit.  Then tell grub what you've just done.  Hit ALT-F2 again and type: 
sudo update-grub  
Then reboot and hope it works.  

I re-emphasize my inexperience and urge users to read the above with that in mind.  Comments, suggestions and corrections are welcome.

---

### Post by dtset on 2010-03-12
Final advice for noobs: do some serious backing up before you attempt to install a new OS.  Consider Macrium for a disk image of the OS and back up your data to an external hard drive or a bunch of DVDs.  

Then to be extra safe, disconnect the external hard drive when you install Ubuntu.

---

### Post by dtset on 2010-03-13
Final details.  My problem was that NVIDIA video cards don't place nicely with Ubuntu's ACPI (Advanced Configuration and Power Interface).  The patch involves setting ACPI=off during bootup with the Live CD (via F6) and with grub 2.   For some reason I could boot up the 32 bit LiveCD Ubuntu directly, IIRC.  

Here are my specs:
Ubuntu 9.10 64 bit desktop 

[SIZE=2]2.00 gigahertz AMD Athlon 64 X2 Dual Core
[/SIZE][SIZE=2]NVIDIA GeForce 8400 GS [Display adapter]
[/SIZE][SIZE=2]BIOS: Phoenix Technologies, LTD 6.00 PG 10/20/2005 
[/SIZE][SIZE=2]3070 Megabytes Usable Installed Memory[/SIZE] 
[SIZE=2][SIZE=2]NVIDIA nForce 10/100/1000 Mbps Ethernet 
[/SIZE][/SIZE][SIZE=2]DELL 2408WFP [Monitor] (24.0"vis)[/SIZE] LCD

---

