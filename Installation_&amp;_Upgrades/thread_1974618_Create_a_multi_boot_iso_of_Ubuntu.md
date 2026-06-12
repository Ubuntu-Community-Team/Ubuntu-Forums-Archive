---
title: "Create a multi boot iso of Ubuntu"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by FLMK on 2012-05-06
Hi everybody,

I wanted to create a multi boot DVD with all version of Ubuntu 12.04 (Desktop x86&x64 and Server x86&x64) .

But I have a problem.

My system crash after the Ubuntu splash (where it shows "12.04" with dots).

Here is the screenshot of my problem:

[IMG]http://img339.imageshack.us/img339/9679/ubuntum.png[/IMG]

Does anyone have an idea about the problem?

Can you help me please?

Thanks in advance.

Bye.

---

### Post by oldfred on 2012-05-06
You were in Tutorials & Tips which is moderated as it is for giving instructions not asking for help. Moved & approved as a question.

Not sure if you can get server to work. I tried with a multi-boot grub2 loopmount on a USB flash drive and server just did not want to boot correctly. 

I used to use CDs for installing. Then found I could put many ISO on one flash drive and boot with grub2's loopmount. I then do not have to burn another CD with each ISO update.

CD/DVD multiboot
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

If you want USB flash:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub4dos
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by FLMK on 2012-05-07
Oh, I'm sorry.

I used to use Grub4DOS on a USB key and it work very well to boot on several isos.

But right now, I wanted to create a multi boot DVD to pass it on because a DVD is less expensive than a usb key...

OK for the server version, but with the desktop version, should it work (on a multi boot DVD)?

---

### Post by oldfred on 2012-05-07
I use grub2, but some of the multiboot scripts do use grub4dos.

this site has a long list of Linux systems you can boot. They include Ubuntu and maybe the way they do it will work with a server version.

[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

---

### Post by FLMK on 2012-05-07
Will this system work on a bootable DVD (with 4 versions of Ubuntu)?

I've ever seen this website, but it seems it is able to create a bootable with several utilities, not several same system (but I've not tried it).

If you tell me that you can create a DVD with 4 versions of Ubuntu, I'll try.

Thanks in advance for your help.

---

### Post by oldfred on 2012-05-07
I have not tried it as I mentioned before I now prefer USB flash as I can easily update. It seems all the installs I have on the USB update at different times so I am constantly updating.

I only burn an occassional CD now, just to have one more way to boot.

---

### Post by drtheradio on 2012-05-08
I would copy and Paste then edit as needed

sudo mkisofs -V "Your_label" -L -J -v -R -o /home/USERNAME/Documents/YOURNEWISO.iso \-b BOOTFOLDER/isolinux.bin -l -c BOOTFOLDER/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table  /home/CD_ROOT    

 <(your folder where your ((CD_ROOT)) cd files are)

Took me awhile  to figure out how to get it to work. the \ before the -b (\-b) and I was not root. But it works ASOME for me..
 
Use Vbox to test save cd's...........

BOOTFOLDER can just be     /boot.cat if boot.cat and isolinux.bin are at the bottom dir
i think you would not even put / just boot.cat

make a folder name it what ever you want..  Replace CD_ROOT with it.
and with your output where ever.
your folder has to have isolinux.bin or syslinux have only tested isolinux.

YOU have to be ROOT And you have to be  at the bottom Dir. 
sudo -i
cd /


I made a MUTIBOOT DVD 8.5GB with 11 different os's
clonezilla,puppy,lighthouse.Gparted,Remastersysbackup.,etc
I also  turned a 500 gb hard drive to a  multi Bootable.

---

### Post by drtheradio on 2012-05-08
Wait your problume is your boot loader
I HAVE HAD THIS SAME ISSUE!
here's how to fix
initrd.img loads and looks for live folder
you need to extract the initrd.img files for all of the live cds you want.
mv initrd.img initrd.gz
gunzip initrd.img
sudo mkdir temp
cd temp
cpio -id < ../initrd
cd scripts
nano live  ...i think 
edit  where it says "live" to the new folder Name is
then ctrl  X   then Y then
find . | cpio --create --format='newc' > /home/initrd
then
cd /
cd home
gzip initrd
mv initrd.gz initrd.img
then copy to boot dirctory.
then move on to the next

.xz you my come across and you have to use xz -d
and xz -9 --check=crc32 to compress sometimes


now to make them all able to install off the cd 
you might have to edit the scripts some more search for the install dir in the scripts
and changes as needed.

---

### Post by FLMK on 2012-05-10
Hi, thanks for answers.

I haven't tried this yet because I don't have time for this moment.

I'll try this as soon as possible.

Thanks a lot.

I'll be back here to give my feedback.

Bye.

---

### Post by FLMK on 2012-05-11
I've succeeded in extracting the initrd.lz, but I can't find the "live" file.

[IMG]http://img842.imageshack.us/img842/268/initrdlz.png[/IMG]

In the script folder, I have this:

[IMG]http://img215.imageshack.us/img215/6475/scripts.png[/IMG]

This is what I've.

Where can I change the path of my system, to allow the initrd to load the right folder that contain my system?

PS: I'm working with an Ubuntu 12.04 LTS Desktop x86 iso...

Edit:

I think I've found what you were talking about: the "LIVE MEDIA PATH".

It was in the casper file in "scripts".

[IMG]http://img29.imageshack.us/img29/6338/caspers.png[/IMG]

I've modified it but right now, I'm blocked. I can't create the initrd.lz...

I've used the help of this website: [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd) and specially the "Modify the initrd" section.

But when I'm in the root of my initrd working space, I use this command:
find . | cpio --quiet --dereference -o -H newc | lzma -7 > ~/new-initrd.lz

It does not work.

I've this error: 

[IMG]http://img545.imageshack.us/img545/5228/erreurt.png[/IMG]

It says an error which means (approximatively): "cpio: ./etc/ld.so.conf.d/i386-linux-gnu_GL.conf: Error of the function : stat: No file or directory of this type"...

Please, help me.

---

