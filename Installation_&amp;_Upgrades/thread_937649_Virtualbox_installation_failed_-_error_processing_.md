---
title: "Virtualbox installation failed - error processing /tmp/virtualbox-2.0_2.0.2"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by jimseg on 2008-10-04
Hi,

I was sucessfully running Virtualbox 1.5.6. I then removed 1.5.6 and tried installing virtualbox 2.0.02 by downloading and running the deb package from the sun site.

However I am getting the following error message.

dpkg: error processing /tmp/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_1386.deb (--install):
trying to overwrite '/lib/modules/2.6.24-19-generic/misc/vboxdrv.ko' which is also in package virtualbox-ose-modules-2.6.24-19-generic
dpkg-deb:subprocess paste killed by signal (Broken pipe)


Can anyone help please?

---

### Post by stinger30au on 2008-10-04
im glad im not the only one with this problem

i was about to post about this myself


i will keep my eyes on this and see what happens


i suspect there is another update to come our way to update the kernel for virtual box

---

### Post by stinger30au on 2008-10-07
bump

---

### Post by Brandoon111 on 2008-10-07
> **jimseg said:**
> Hi,

I was sucessfully running Virtualbox 1.5.6. I then removed 1.5.6 and tried installing virtualbox 2.0.02 by downloading and running the deb package from the sun site.

However I am getting the following error message.

dpkg: error processing /tmp/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_1386.deb (--install):
trying to overwrite '/lib/modules/2.6.24-19-generic/misc/vboxdrv.ko' which is also in package virtualbox-ose-modules-2.6.24-19-generic
dpkg-deb:subprocess paste killed by signal (Broken pipe)


Can anyone help please?

I HAVE THE ANSWER!!!!!!!




The VirtualBox binaries can be downloaded from here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads). If the PUEL license is ok for you and there's a package for your distribution, you can install that package. For example, there is a VirtualBox .deb package for Ubuntu 6.10 (Edgy Eft), so if you use Ubuntu 6.10, you can use that package. I've also tested this package successfully on Ubuntu 7.04 (Feisty Fawn), so it seems you can use that package there, too.

To install the VirtualBox .deb package, please open a terminal window (Applications > Accessories > Terminal) and become root:

sudo su

Then install some prerequisites for VirtualBox:

apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential

Then go to the VirtualBox download page and pick the right .deb package for your Ubuntu version and download it to your system:

cd /tmp
wget [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb)

After the download has finished, you can install VirtualBox like this:

YOU HAVE TO DO THIS!!!!!

dpkg -i --force-overwrite /.../.../..../virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb



You might get asked the following questions:

Do you agree with the PUEL license terms? <-- Yes
Should the vboxdrv kernel module be compiled now? <-- Yes

That's it already. You can now find VirtualBox under Applications > System Tools: 


SPREAD THE WORD!!!!!!:guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by stinger30au on 2008-10-14
thanks for your reply, and i would love to say this has worked, but it has not.

im about ready to backup my data and FASA this pc

Format
and
start
again


i did everything you said and got no errors

if at the end of at all i type in to shell

virtualbox

it says it can find it

i have restarted the pc as well

and if i look in applications->system tools

virtual box is not listed either

---

### Post by stinger30au on 2008-10-15
well, i decided to bite the bullet and FASA my pc


again it failed to work untill i followed your instructions *EXACTLY* and now it works fine


Thanks you

---

### Post by okubax on 2008-10-25
the solution is quite easy: remove the package virtualbox-ose-modules-2.6.**-**-generic and then install the virtualbox.deb package.
hope this helps

---

