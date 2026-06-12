---
title: "HDD Config"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by drew boardman on 2011-05-01
Hi

I have an EeePC 901, with a 4gb SSD and a 16gb SSD installed.

Trying to get Natty installed and hit a few problems not least of which, that it won't fit on the 4gb drive!

However in my BIOS setup under HDD config it says
Secondary Master=4gb
Secondary Slave=16gb

I have no other devices attached.  Why aren't they Primary? And I can't seem to switch them round.

Thanks

Drew

---

### Post by JRV on 2011-05-01
Don't worry about that.

When the installer gets to the place to partition select manual partitioning.
Create a single ext4 partition using the entire 4 gig SSD with mount point /.
Create a single ext4 partition using the entire 16 gig SSD with mount point /home.
You do not want to put a swap partition on the SSD because it can cause too many writes and use up the life of the SSD.

Here is a list of tweaks to limit writes to the SSD to increase it's life and improve performance:
> Four Tweaks for Using Linux with Solid State Drives

Published in September 4th, 2008
Posted by Tom in tips

SSDs (solid state drives) are great. They&#8217;re shock resistant, consume less power, produce less heat, and have very fast seek times. If you have a computer with an SSD, such as an Eee PC, there are some tweaks you can make to increase performance and extend the life of the disk.

   1. The simplest tweak is to mount volumes using the noatime option. 
      By default Linux will write the last accessed time attribute to files. 
      This can reduce the life of your SSD by causing a lot of writes. 
      The noatime mount option turns this off.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Ubuntu uses the relatime option by default. For your SSD partitions, 
      replace relatime with noatime in fstab. Reboot for the changes to take effect.

-------------------------------------------------------------------

   2. Using a ramdisk instead of the SSD to store temporary files will speed things up,
      but will cost you a few megabytes of RAM.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Add this line to fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

      tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

      Reboot for the changes to take effect. Running df, you should see a new line with /tmp mounted on tmpfs:

      tmpfs 513472 30320 483152 6% /tmp

--------------------------------------------------------------------------------------------------------

   3. Firefox puts its cache in your home partition. 
      By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
      Complete the previous tweak to mount /tmp in RAM, and you can put the cache there as well.

      Open about:config in Firefox. Right click in an open area and create a new string value 
      called browser.cache.disk.parent_directory. Set the value to /tmp/$USER/firefox-tmp.

-------------------------------------------------------------------------------------

   4. Turn off Journaling in EXT4

      First thing's first, we can confirm that our ext4 partition is running a journal with

        sudo dumpe2fs /dev/sdaX | grep has_journal

      Disabling journaling is rather easy, the only drag is that to make structural changes to a filesystem, 
      the filesystem cannot be mounted with read/write privileges. So, run a live cd and hit

        sudo tune2fs -O ^has_journal /dev/sdaX

      And it's done. Now when you boot, the change will be noted and the disk will be checked for errors. 
      When the system is finally up we can run this again to confirm that in fact ext4 is running without a journal

        sudo dumpe2fs /dev/sdaX | grep has_journal

      should now return nothing.

      With this quick fix, no more constant IO peaks. I can now watch youtube videos without constant freezes.


By putting /home on the 16 gig drive my Natty installation uses about 2.8 gig of the 4 gig drive.

You can save about 50 meg of disk space by installing localepurge with the command:
```

sudo apt-get install localepurge

```
During the installation it will list all the languages and ask you to check the ones you want to keep.  For US English you would want to keep en and everything beginning in en_US.
After installation run it with the command:
```

sudo localepurge

```
localepurge is slow, dpkg calls it automatically at the end of any install or update, often multiple times.  But it is worth the wait on a small drive.

---

### Post by drew boardman on 2011-05-01
Thanks for that. 

Natty won't  install at the moment to the 16gb drive, I think there is a bug. That's why I asked about the HDD configuration. The tips are great though and when it's installed I'll be using them. 

Drew

---

### Post by JRV on 2011-05-01
Try using the alternate install CD.
I have found that it will usually solve install problems.

---

### Post by drew boardman on 2011-05-01
Thanks I'll try that for the install. Any other thoughts on the primary/secondary master and slave query?

Thanks again

Drew

---

### Post by JRV on 2011-05-01
I can't check the primary-secondary thing because I switched out my 16 gig SSD for a SATA SSD which changes it.

If using the alternate install disk does not solve your problem try asking the question on [http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

