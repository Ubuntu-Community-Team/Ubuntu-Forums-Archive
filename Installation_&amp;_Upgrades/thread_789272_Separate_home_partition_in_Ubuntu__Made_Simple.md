---
title: "Separate home partition in Ubuntu  Made Simple"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by criskat777 on 2008-05-10
Introduction
This guide is for creating a separate /home partition if you already installed Ubuntu without a /home partition (i.e., /home is just a folder inside your / partition). If you have not yet installed Ubuntu but want to create a /home partition before installing (a very good idea, by the way), use this guide. If you want to know more about partition planning, read this.

Important Disclaimers

    * Even though I created the form of this tutorial, the steps outlined in it are taken directly from a text-only (command-line-driven) guide for this process.
    * I and others have been successful in creating a separate /home partition using this tutorial, but there are many who have had difficulty being successful with the process. If you are not confident in what you're doing or in repairing or recovering from this process should anything go wrong, then do not attempt the instructions outlined here. I cannot help you troubleshoot problems that result from following this tutorial.
    * Creating a separate /home partition involves resizing at least one existing partition. In almost all cases, the resizing of partitions does not result in data loss, but there still exists a (however small) risk of data loss, so you should back up your important data before attempting to resize your partitions.
    * The tutorial was created a long time ago using an older version of Ubuntu. The same principles should still work for recent versions of Ubuntu, but you may see little discrepancies in form (for example, the use of UUIDs in the /etc/fstab file).

Requirements
You must use a live CD for this process, for two reasons:

   1. In order to resize your existing / partition, it needs to be unmounted. The only way to unmount it is for it not to be in use, which means you can't boot to your regular Ubuntu installation while resizing it... which means you need a live CD
   2. If you screw up your installation by accident, you can use the live CD to restore your old settings and, in the worst situation, at least recover your important files

I'm using the example of a Ubuntu live CD and GParted, but you can very well use QTParted on Knoppix or DiskDrake on PCLinuxOS.

Making the new partition
Boot up a live CD and in your live session, install GParted (and ntfsprogs, just in case you're carving a partition out of an existing NTFS partition... before resizing an NTFS partition, though, make sure you defragment it in Windows). You can use Synaptic Package Manager to install it (Don't know what Synaptic is? Look here, or if you prefer the command-line, go to the terminal and type in
sudo apt-get update && sudo apt-get install gparted ntfsprogs

Then, press Alt-F2 and type
gksudo gparted

In GParted, find the partition you want to resize in order to make room for your upcoming /home partition. In this case, I'm resizing /dev/hda5, but your partition may be different. Be sure to keep track of the names of your partitions--these names are very important (/dev/hda1, /dev/hdb1, /dev/sda2, etc.).

Right-click on the partition and choose the Resize/Move option.

Choose the new size you want.

Then, in the new empty space, right-click and select New.

Choose to create the partition as Filesystem ext3.

When you're satisfied with your new partition layout, click Apply

Once the changes have been applied, make note of the partition name of your new partition and then quit GParted.

Now, in my example, my original partition that I shrunk was /dev/hda5, and it created a new partition called /dev/hda7, and my /home folder lives on /dev/hda1. It's very important that you substitute in your own appropriate partition names for the ones I'm using--you most likely will have only two partitions you're dealing with--the one you shrunk and the newly created one.

Using the new partition
Now, back in the terminal, I'm going to mount /dev/hda1 and /dev/hda7:
sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new

Now we're going to back up the /home directory on the old partition and move it to the new partition:
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Yes, one of those lines looks really complicated--please type it as is--or, if you're unsure of your typing skills, copy and paste it into the terminal. Believe me--the command is necessary.

Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2

Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition.

If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be, then go ahead and delete the backup of home:
sudo rm -rf /home_backup

If when you reboot it gives you a error that reads something like this "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be own by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."
don't panic do the following (replace criskat777 with your user name)

sudo chmod 644 /home/criskat777/.dmrc
sudo chown criskat777 /home/criskat777/.dmrc
sudo chmod -R 700 /home/criskat777
sudo chown -R criskat777 /home/criskat777

What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things.

Boot up the live CD, go to a terminal, and type:
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

Then, reboot. 

This how to was made from info found on two diffrent fourms
so the credit is all theirs i just conbined them so that it would cover posible problems. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

---

