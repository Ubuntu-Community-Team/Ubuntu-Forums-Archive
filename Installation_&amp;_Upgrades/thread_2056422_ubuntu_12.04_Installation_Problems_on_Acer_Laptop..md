---
title: "ubuntu 12.04 Installation Problems on Acer Laptop.."
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by Jitarth on 2012-09-11
I got a new acer laptop loaded with windows 7 Professional. i installed Ubuntu 12.04 from a usb drive and it has been installed. but when i boot my pc there is no grub menu which helps me to choose between ubuntu or windows 7. windows 7 directly loads ub without any grub menu or reference to ubuntu.

I tried reinstalling grub on my pc using the live usb but it was unable to write the grub to my harddisk. i had mounted all the partitions.

I have not been able to boot into the ubuntu installed on my harddisk. though its working fine from the pd. 

My laptop model is acer travelmate p643, i3 processor 4 gb ram and intel hd 3000 graphics..

Some Help would be appreciated :)

---

### Post by abhicr on 2012-10-02
hey guys!
even i'm facing the same problem... :( except that I installed from a CD...
could someone help please...?

-abhi

---

### Post by abhicr on 2012-11-15
Hey Jitarth, found a fix for the ACER problem here:
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

btw, here's the complete procedure too:
here's the link which helps in installing boot-repair:
Boot into Ubuntu using the Live-CD (Try Ubuntu).
1. in the [boot-repair webpage]("https://launchpad.net/~yannubuntu/+archive/boot-repair-dev"), expand the "Technical details about this PPA" and copy the displayed lines.
2. In the update manager->settings->other software->add
paste the copied content in the popup. The PPA will now be added for installing boot-repair (if not already installed).

alternatively, here's the command line:
> sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair

3. In case you get a missing key error (GPG key error), copy the contents of [this page]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x32B18A1260D8DA0B") into a file with a .ppk extension.
4. In update manager->settings->Authentication->add key, point to the .ppk file that you just created.This should ensure that apt will install boot-repair.
5. Once boot-repair is installed, it is a GUI that will guide you through the installation process.
* either Recommended repair mode or use the advanced options mode as is convenient. *I used the Recommended Repair mode, and the problem was fixed.

---

