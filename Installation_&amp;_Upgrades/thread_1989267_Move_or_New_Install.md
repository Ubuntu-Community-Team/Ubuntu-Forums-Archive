---
title: "Move or New Install?"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by sturdy on 2012-05-28
Precise presently resides on an older PATA drive that is starting to overheat. I would like to give it a new home on a new SATA drive. Is there an easy way to do this or should I reinstall Precise and all apps (ouch) on the new drive? TIA.

---

### Post by drs305 on 2012-05-28
A clean install might in the long run be easier. If you do it that way, you can install Synaptic (if not already installed by you) and create a list of installed apps which you can import into your new machine. Synaptic > File > Save Markings As (and tick the lower left Save Full State).

If you want to transfer, you could make an image with something (I use fsarchiver) and copy it over to the new machine. Copying works for me since my installs are less than 5GB because all my data is stored elsewhere. On the new machine, you would need to edit /etc/fstab  to make sure the UUIDs are correct and probably manually boot into GRUB 2 the first time, but it wouldn't be extremely hard to do it this way.
If you are interested in fsarchiver:
[http://ubuntuforums.org/showpost.php?p=11968939&postcount=3]("http://ubuntuforums.org/showpost.php?p=11968939&postcount=3")

---

### Post by sturdy on 2012-05-28
> **drs305 said:**
> A clean install might in the long run be easier. If you do it that way, you can install Synaptic (if not already installed by you) and create a list of installed apps which you can import into your new machine. Synaptic > File > Save Markings As (and tick the lower left Save Full State).

[http://ubuntuforums.org/showpost.php?p=11968939&postcount=3]("http://ubuntuforums.org/showpost.php?p=11968939&postcount=3")

Thanks drs305,
Can I assume that Synaptic > File > Read Marking will download ind install the packages?

---

### Post by drs305 on 2012-05-28
> **sturdy said:**
> Thanks drs305,
Can I assume that Synaptic > File > Read Marking will download ind install the packages?

Yes, just make sure when you originally save them you tick the Save Full State box. And make sure you export the file to a partition that isn't overwritten by the new installation.  ;-)

---

### Post by sturdy on 2012-05-28
Thanks again, I'll give it a try.

---

### Post by drs305 on 2012-05-28
You can use dpkg's "--get-selections" to export and then "--clear-selections" and "--set-selections" options from a terminal to do the same things, but many users are more comfortable with using a GUI app these days.

The file you create with Synaptic is just a text file, so open it and look for a particular package you installed. That should give you a bit of comfort knowing you have a proper listing.

---

### Post by sturdy on 2012-05-28
Partial success...I did a Precise Alternate install and everything seemed to go okay. Files are located on the new drive with a seperate home partition. But Grub seems to have not found thing properly. I have only one boot option that boots into the original (old) drive. Do I need to disconnect the old drive before installation or is repair possible?

EDIT: I just saw your Boot Repair link so will give that a try later. Gotta go now...thanks.

---

### Post by drs305 on 2012-05-28
> **sturdy said:**
> Partial success...I did a Precise Alternate install and everything seemed to go okay. Files are located on the new drive with a seperate home partition. But Grub seems to have not found thing properly. I have only one boot option that boots into the original (old) drive. Do I need to disconnect the old drive before installation or is repair possible?

EDIT: I just saw your Boot Repair link so will give that a try later. Gotta go now...thanks.

It's possible your BIOS is still booting the old drive, whose MBR points to the old GRUB files. If you change the BIOS to boot from the new drive first it may pick up the new installation's GRUB menu. 

If not, Boot Repair should fix things for you. Just install GRUB to the new drive and not to the Ubuntu partition itself. Ensure that your BIOS looks at the new drive first and it will probably work.

---

### Post by sturdy on 2012-05-30
I spent all of yesterday chasing my tail...boot-repair would ID the boot drive by UUID then GRUB always failed to find it. Then (by accident) I discovered the BIOS was not properly IDing the drives. Strange because everything had worked for the last three years. Once corrected, boot-repair worked perfectly and now all is well.

I do have another question: My new install is AMD64, old is i386. Can I simply copy my old home directory to the new install? Will the various hidden dir be compatible?

Thanks much drs305 for the assist.

---

