---
title: "Upgrading to 8.10"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-10-03
I started using Ubuntu with the release of Hardy Heron, so I don't know the experience of upgrading. I know it's not time yet, but when this time comes I'd like to know what to expect. Is it wise to do a backup? Is upgrading easy or do I need to reinstall? Will current customizations hold?

---

### Post by Sorivenul on 2008-10-03
> **JustAnotherVagueAnon said:**
> I started using Ubuntu with the release of Hardy Heron, so I don't know the experience of upgrading. I know it's not time yet, but when this time comes I'd like to know what to expect. Is it wise to do a backup? Is upgrading easy or do I need to reinstall? Will current customizations hold?

Upgrading is a heavily debated issue.  You can, if you like, continue to simply update your Hardy install through the point releases (8.04.2, 8.04.3, etc.).  A backup is always recommended whenever you do anything major to your operating system, in my opinion.  LaRoza is working on [SysRes]("http://ubuntuforums.org/showthread.php?t=678665"), which might fit your needs, or there are other ways to back up your important data.

Upgrading is very easy, should you decide to do it.  The Update Manager should notify you and ask if you would like to upgrade to the latest distribution version.  Alternatively, changing all the instances of "hardy" to "intrepid" in the /etc/apt/sources.list file and then doing:
```
sudo apt-get update
```
followed by
```
sudo apt-get dist-upgrade
```
should work.

From my experience, personal customizations should hold, but doing a backup of your settings/system will give you a reference if they don't.

In short, no need to reinstall, and no need to upgrade if you really don't want to - Hardy will continue to get more stable, and after Intrepid, the next LTS is only 6 months away! 

Hope this helps you.  Good luck!

---

### Post by Sef on 2008-10-03
> Is it wise to do a backup?

Always.  There is no guarantee that all will go well.


>  Is upgrading easy or do I need to reinstall?

You can do either.  There is less likely to be problems with a clean install than an upgrade.


>  Will current customizations hold?

If you upgrade, they will hold.  If you reinstall, then they will be formatted over.

---

### Post by MepisReign on 2008-10-07
Well, definitely back up is the rule of thumb. Now, I have a question, is it possible to make an image of an actual installation (settings, applications installed and so on)?
I always keep my personal data on DVD media (just in case). But what I would like to do is have the very same OS with all the tweaks and configuration, on a spare hard drive. Would that be possible?

Best Regards

LinuxReign

---

### Post by Sorivenul on 2008-10-07
> **MepisReign said:**
> But what I would like to do is have the very same OS with all the tweaks and configuration, on a spare hard drive. Would that be possible?
[partimage]("http://www.partimage.org/Main_Page")
Or, as mentioned before:
[Remastersys]("http://www.remastersys.klikit-linux.com/")

---

### Post by Spaceman9 on 2008-10-08
[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

"Upgrading from Ubuntu 8.04

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions."

It's best to wait until Ubuntu 8.10 is finished. Alpha, beta and RC are not stable. The finished 8.10 will be posted for download October, 30 2008.

---

### Post by robert shearer on 2008-10-08
> **MepisReign said:**
> Well, definitely back up is the rule of thumb. Now, I have a question, is it possible to make an image of an actual installation (settings, applications installed and so on)?
I always keep my personal data on DVD media (just in case). But what I would like to do is have the very same OS with all the tweaks and configuration, on a spare hard drive. Would that be possible?

Best Regards

LinuxReign

Another vote for Remastersys.!
And it even puts it on a bootable cd/dvd (just like the Live Ubuntu desktop cd) that you can use to re-install or even install to a different system.

Note that it won't save your graphics card setup.

Also note this from the Remastersys forum..

> You can use Remastersys to backup a fully updated system.

  The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
  Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes.  Mine generally is just a bit over 1 gig. 
  Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.  

Also look for the following folder:  /var/cache/apt/archives.  That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system.  The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason.  You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more. 

---

