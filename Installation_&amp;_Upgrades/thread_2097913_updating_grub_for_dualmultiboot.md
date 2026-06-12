---
title: "updating grub for dual/multiboot"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by Flaggmann on 2012-12-24
I had ubuntu studio 12.04 LTS installed and working OK; still does.  I installed win xp pro sp3 and did grub update and menu list shows both OS's. Had trouble with asus drivers for xp so trashed win and went to centos 6.3 instead on that drive. However ubuntu grub does not detect or show the centos boot as an option, and the centos does not detect of show ubuntu as a menu list option.

win xp pro sp3 having been removed from menu and grub updated ok.

does anyone have an example grub.cfg  file syntax, and a procedure for either of the systems that I can use to get one or the other grub menu list to show both linux distros as boot options so I don't have to keep going into setup and changing the boot drive.

Thanks

---

### Post by slooksterpsv on 2012-12-25
Here's what I would try:

Boot into either OS (Ubuntu or CentOS). Mount the other via terminal:

Example: Ubuntu is on sda1 Centos is on sda3, sda5 is swap that is shared between both.

I would mount CentOS, go into and open /media/<centos_partition>/boot/grub/grub.cfg

Find the section where it says for booting Cent OS:

e.g. menuentry 'CentOS 2.6.......'
{
....
}

Copy that and paste it after your Ubuntu menuentry in /boot/grub/grub.cfg file and see if that works.

Reason being is the root hdd will be different, so ubuntu may be on 0,0, while centos may be on 0,2.

If not, make sure they both are using the same version of Grub (grub 2 vs grub 1)

---

### Post by carl4926 on 2012-12-25
I've had this before

From Ubuntu If you mount the / partition for CentOS
Then run

```
sudo update-grub
```

---

### Post by Flaggmann on 2013-01-15
no didn't work thnx fer time anyway. seemed logical and simplest

---

### Post by Flaggmann on 2013-01-15
grubs too different to direct paste  thnx fer ur time anyway

---

### Post by darkod on 2013-01-15
Did you maybe install centos with LVM?

The ubuntu desktop OS doesn't have the package lvm2 included by default and I am not sure it can detect it. Maybe that is the reason update-grub is not picking it up.

If you list your partitions with fdisk or parted, so you see any LVM partitions?

---

### Post by Flaggmann on 2013-01-15
no no lvm both drives have 3 parts, root, home and a separate swap  In the past I have installed centos 5 on 1st HD first, then added ubuntu after with centos drive still installed and it gets detected on install so I thought I could access the module, script or pgm that installer uses in ubuntu and just run the disk detect portion but no such luck

---

### Post by Flaggmann on 2013-01-15
grubs are different as well one is legacy and the other grub 2 so copy paste isn't simple without some sort of text manipulation but can't find established syntax example to use going either way

---

### Post by darkod on 2013-01-15
The grub version that ships with each distro is not important. Grub2 coming with ubuntu is quite good in detecting other OSs and should make an entry in the boot menu.
Are you running your grub2 in original form? You didn't maybe disable the os-prober script earlier and forgot about it?

From ubuntu, can you please post the output of:
```
sudo parted -l
sudo update-grub
```

---

### Post by oldfred on 2013-01-15
Post full bootinfoscript so we can see all the details.

       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

