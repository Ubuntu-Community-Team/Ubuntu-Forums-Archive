---
title: "Error setting up encrypted RAID swap"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2010-05-02
This is my first time attempting to do this with Linux, and I wasn't following a particular guide, just figuring it out as I go... perhaps I should have... but here's the situation.  I have an old computer I use as a VMware ESXi 3.5 server.  It's known working and I've been running other VMs in it for a while.  I've decided I want to add an Ubuntu server to the mix, mostly as a learning experience and for possible use in a production environment later.

I have two physical hard drives in the ESX server.  Since I have no redundancy at the hardware level in this old rig, I want to set up software RAID.  For learning purposes, I also would like to encrypt everything to the extent possible (I understand /boot cannot be encrypted).  I've given the VM two hard drives, one stored on each physical hard drive.  The first one looks like this:


[LIST]
[*]100MB used as RAID
[*]20.4GB used as RAID
[*]1GB used as RAID
[/LIST]
The second virtual drive has an identical size and layout.  RAID volumes are configured as follows:


[LIST]
[*]100MB used as RAID1 EXT4 mounted as /boot
[*]20.4GB used as RAID1 for encryption
[*]1GB used as RAID0 for encryption
[/LIST]
After setting up encryption on the latter two RAID volumes, the 20.4GB is used as EXT4 and mounted as /.  The last one is used as SWAP.

As I'm leaving the partitioner during setup, I get this error:

> The attempt to mount a file system with type swap in Encrypted volume (md2_crypt) at none failed.

You may resume partitioning from the partitioning menu.

Do you want to resume partitioning?
<Go Back>                                 <Yes>   <No>
What was my mistake here?

---

### Post by Karl1982 on 2010-05-02
Well, I thought I'd try simply bypassing it and hopefully it would pick up the swap area when it boots, but no such luck -- the installer won't let me continue while this error is present.  My installation is on hold until I can resolve this.  Any help is much appreciated.

---

### Post by Karl1982 on 2010-05-02
I deleted the disks the virtual disks from the ESX server and gave it new ones, started over as clean as it could possibly be, made sure the drives were set up exactly the same in every way.  I'm still getting the same error.

---

### Post by Karl1982 on 2010-05-02
Well, I finally caved.  I was able to bypass the problem by setting up the third partition of each disk as an individual encrypted swap area, rather than a combined RAID0 encrypted swap area.  Whether this is better or worse depends on how smart it is about I/O between disks.  If it was going to split reads between the mirrors, which I was hoping it would, then it would make sense to have a striped swap area.  I'm just afraid it's going to read everything from one disk of the mirror and try to do half of its swapping on the opposite disk.

I would still like to know what I was doing wrong originally, though.  Can anyone help me with this?

---

### Post by Karl1982 on 2010-05-03
Now this is strange.  After proceeding with the installation, I was prompted for settings for postfix, which I was never asked whether I wanted or not.  I was never given the menu to choose components to install.  After configuring postfix for local only, the installation failed.

> The failing step is: Install the base system

Maybe I'll just forget about storage redundancy and encryption for now if no one has anything to say about this...

---

### Post by Karl1982 on 2010-05-04
I decided to give it one more shot and have Ubuntu show me how it does guided LVM with encryption, then I copied that scheme manually, but with software RAID at the bottom.  It looks like this:


[LIST]
[*]Two hard drives, each 21.5GB.  They have identical partition tables.  One 256MB primary, and the remaining 21.2GB as one logical.
[*]I applied software RAID-1 to both, resulting in MD0 and MD1, respectively.
[*]MD0 is formatted ext2 and mounted as /boot.  No further changes to MD0.
[*]MD1 is configured for encryption.
[*]MD1_crypt is configured for LVM, creating two volumes, 20.2GB and 1GB.
[*]The 20.2GB LVM volume is formatted ext4 and mounted as /.
[*]The 1GB LVM volume is used as swap.
[/LIST]
This is exactly how guided LVM with encryption decided to use my drive, except without the underlying software RAID.  The error I got this time is:

> The attempt to mount a file system with type ext2 in RAID1 device #0 at /boot failed.

You may resume partitioning from the partitioning menu.

Do you want to resume partitioning?  <go back|yes|no>It wasn't a swap space this time.  I get the feeling the software RAID is what's killing it.  What I intend to do now is remove one drive and let it install via guided LVM+crypto, with no redundancy... I'll report back with what happens.

---

### Post by JayRobert on 2010-05-05
I have set up a RAID5 on 3 640GB disks for /home and /usr, plus a non-RAID 40GB SSD for /boot, /, swap, /opt, /srv, and /tmp,  with LVM for each except /boot and and encryption for each except /boot and /.  I was like you, just started in at it without reading much, finally got it to work.  Having done about 5 or 6 installs since January, I have gotten kind of good at it.  Don't give up!

(Note that the partitioner will restart in between each of these steps.)

The order I have found to work best in the partitioner is to:
1.  Set up RAID;
2.  Set up LVM volume groups and logical volumes (it helps to name them with whatever partition you intend to use them as; e.g., name / as 'root' in the partition set up screen, name /home 'home' (without quotes of course), etc.);
3.  Select 'set up encryption volumes' (or something like that) from the partitioner menu, and encrypt the logical volumes (the encryption doesn't actually happen until after partitioning is finished - you will be prompted for passwords); 
4.  Select the encrypted logical volumes and assign a file system, mount point, name, etc.

If you designate a swap area before encrypting, you will get an error,  since an unencrypted swap area might potentially allow your encrypted  data to pass into the clear, which of course defeats the purpose of  encryption.  This is why you will not designate the swap area until step 4.

Once you exit the partitioner and the install is complete, you will get  prompts for passwords for each encrypted volume on boot up.  Swap is always first, then the others will come up in no particular  order, which is why Lucid's new scheme (see below) prevents using multiple passwords  - unless I missed something in the documentation that would allow me to  see which encrypted volume I am unlocking.

Sure, it's kind  of a pain to enter a 20+ character password eight times on start up (if you are as partition-mad as I am), but it's worth it.  I mean, you're paranoid, aren't you?  You don't trust other people not to try to see what's on your hard drives and then try to steal it or screw it up or whatever, right?  So go for it, and think up funny answers to people who ask you why you would want to configure your system that way.

Actually, in practice, if you have eight encrypted partitions, you will have to enter your 20+ character password more like nine or ten or eleven or even fourteen times, since for some reason volumes don't always mount the first time you enter the password.  Just keep entering it until you run out of prompts.  Occasionally in Karmic it would jump ahead after entering only one or two characters of the password - that volume always got another prompt.

If you get a password wrong, the screen will freeze with a bunch of text crap (yeah, I know, "error messages") ending in 'terminated with error 1.'  Translated, this means 'do a hard reboot and start over.'

Once the volumes are unlocked and mounted, you will get your regular password prompt as usual.

PLEASE NOTE:  If you are using 10.04 Lucid Lynx, you will want to use the same  password (preferably 20 characters or more) for each and every volume, since for  some reason the developers changed the boot screen prompts in Lucid so that they do not tell you which  volume you are unlocking.  (Developers: please change this!!)  (Yes, I'll find the proper thread and post my request there, but not tonight.)

9.10 Karmic does list the UUID for each volume on the boot screen at the password prompt, which, if you name each volume the  same as the partition (without the forward slash), allows you to use  different passwords for each encrypted partition, providing further  security but also requiring more memory from your gray matter, and perhaps less security if all that makes you think about writing down the passwords and thus opening yourself to a physical security risk that does not exist if you can remember just one password for all volumes / partitions.

I haven't found much discussion of encrypting RAID LVM disks on the ubuntu forums - apparently, it's too much work for most people, or they just don't care, or whatever.  So, cheer up - there is at least one other who is crazy like that here.  And if you figure out how to do it during the Gentoo install, please let me know - I tried, and made a hash of my drives.  At least ubuntu is *relatively* easy.

---

### Post by Karl1982 on 2010-05-05
Many thanks for the info.  I am indeed using 10.04 LTS, I guess I forgot to mention that up front.  I shall persevere.  I've gotten a Windows 2003 server to boot reliably out of dynamic disks that I'd chopped up into several different flavors of software RAID, so I'm sure I can work this out eventually.  I'm assuming of course this is going to be more stable than Windows.

I didn't realize I would have to enter the password at boot.  I suppose I've grown accustomed to using EFS in Windows environments.  It's remarkably hassle-free.  Not that I mind entering passwords... You and I have a symbiotic relationship with passwords... it's just that it may mean something different to me than it does to you.  Are you familiar with VMware ESXi?  (if not, you should check it out -- it's free).  Since the server is virtual, the only way to access its console session is to use the VMware vSphere client to connect to the ESXi server over the network.  I'm assuming of course there's no way to unlock these volumes remotely, via SSH or some other fashion.  I don't actually know.

None of that matters if uptime is good, though.

So if I'm understanding this correctly, what you did differently was RAID -> LVM -> encryption, versus my RAID -> encryption -> LVM.  I was following the partitioner's guided example, which was two partitions, one ext2 for /boot, and one crypto, which was then used for LVM and subdivided into / and swap.  I'm thinking maybe the reason they did that was so entering the password once would unlock both encrypted volumes.  But that doesn't seem to be working for me, so I'll try your way.

I find it highly unlikely that incompatibility with VMware ESX is the cause of my problems, but I suppose I can't rule it out.  And maybe it's a moot point -- in a production environment, I would likely have hardware RAID-5 on the ESX server anyway.  This is the ESX server that sits in my computer room at home with a couple of good old 80GB PATAs.

I do have a 10.04 LTS virtual server running at work, running Nagios on an otherwise purely Windows domain.  But it doesn't contain any sensitive data, so I didn't encrypt it, and the PowerEdge T300 that's running ESX and Ubuntu has hardware RAID-5 underneath it all, so I didn't use software RAID either.  I had absolutely no trouble with that installation.

You know what, maybe I'll also try this at work on a physical box.  We've got a Proliant ML350 sitting around that we virtualized a while back.  It used to run our IP security cameras, but now it's not doing anything.  I'll unRAID the drives and try this with software RAID on it when I have time.

---

### Post by JayRobert on 2010-05-05
Yes, I found RAID -> LVM -> encryption -> assign mount points to work better.  I didn't use the guided example; I went straight to manual.  I haven't tried the guided partitioning, so I'm not sure what they suggest.  I have noticed that there seems to be precious little support in the community for help with software RAID and encryption, though there is a little more support for LVM.  Probably the people that know about it are super-busy with other stuff, since they have skills.

I would have preferred to do it your way, since that would mean one or two passwords for one or two big encrypted volumes that the logical volumes sit on (I'm really not *that* into memorizing eleventeen passwords!), but I couldn't make it work either.  I don't remember how I figured out to try it the other way; I just remember being tired and frustrated and trying one more thing, which thankfully worked.

I am not sure whether it is possible to unlock the volumes remotely,  since I haven't had a need to try it.  (This is a home system, so all  this exercise is really just for fun.  I know, weird.  Hey, I'm a geek,  what'd you expect?)  I did set up a virtual server on my home box (just for fun) but uninstalled it when I decided to completely abandon Windows (at home) a little while back.  I will look into the VMware ESXi when I get a chance - right now I'm still fighting little annoyances with the 10.04 install, and I don't have much time or energy for tackling another virtual install at the moment.

Let me know how it goes!

---

### Post by Karl1982 on 2010-05-05
I failed with this setup (same error, couldn't mount the one used for /boot):


[LIST]
[*]RAID1
[/LIST]
[INDENT]
[LIST]
[*]LVM
[LIST]
[*]256MB ext2 /boot
[*]20.2GB crypto
[LIST]
[*]ext4 /root
[/LIST]
 
[*]1GB crypto
[LIST]
[*]swap
[/LIST]
 
[/LIST]
 
[/LIST]
[/INDENT]Maybe I'm going about this the wrong way.  I decided to try something exceedingly simple, using only one of those three subsystems, just to see if it'd mount and install.  Of the two drives, I made one large RAID1 for /, and one small RAID0 for swap.  That installation appears to be proceeding just fine.  Next I'll try one big RAID1 with LVM layered on top into /, /boot, and swap.  We'll see if that works.

EDIT: Also, what's up with it automatically installing postfix?  Does 10.04 no longer ask you what components to install?

---

### Post by Karl1982 on 2010-05-05
Used the whole disk as RAID1 with LVM containing ext2 /boot, ext4 /, and swap, worked fine.

After that, I tried it without any RAID, leaving the second drive unpartitioned.  I made 256MB ext2 /boot, and the rest as encryption, put LVM on top of the encryption, and created ext4 / and swap.  Also worked fine.

None of this is much of a stretch from what I tried to do originally, so I'm at a loss as to why it's not working.  Can you think of anything else I might try to narrow the problem down?

---

### Post by Karl1982 on 2010-05-05
Well, I finally fixed it, although I still can't quite explain the problem.  You won't believe what it came down to.  What I did was I created all the volumes in the layout I really wanted, told it to use them as what they should be (with the exception of swap which I left unused), and I forced it to commit changes and format them by going back into the LVM menu.  I just hit finish on the LVM menu, then hit go back at the partitioning menu, which brought up the main menu for the installation.  I went to the bottom and told it to abort.  It shut down and rebooted.

When I got back to the partitioning menu, my two software RAID1 volumes were still there, but they were both marked as empty.  I proceeded to set them up again as I had before, and at the very end, gave it the mount points in logical order (ext4 as /, ext2 as /boot, and finally swap).  The installation completed normally, and now it's running beautifully.

What caused me to get the idea to partition, cancel, and then start over and reuse them was that it seems to periodically get a funny idea about what a partition is.  After a while I noticed sometimes after setting up identical partitions on the drives, one of them would be unused, and the one on the other drive would be ext2 or ext4 or something like that.  Almost like it wasn't writing out changes correctly and reading in some old data from the partition table.  I wrote an empty partition table to both disks as my first step every time, so there really shouldn't have been anything like that in there.  I even deleted the virtual disks and gave it a pair of "factory unformatted" clean ones once or twice.

The other oddity I noticed is it prompted me for postfix config options right after installing the base system... then afterward asked me which components I would like to install (LAMP, Mail, OpenSSH, etc...).  Very strange indeed.

Anyway, thanks for all your help.  We may have to compare notes on a few other subjects in the future.  Here's my victory screenshot showing my final partition layout (sdb is off the bottom, but it looks just like sda):

[IMG]http://img.photobucket.com/albums/v394/karl1982/Tech/drive-layout.png[/IMG]

---

### Post by JayRobert on 2010-05-06
That's very interesting!  I didn't take a screenshot when I finished, but it looked different; I think the encrypted volumes showed the mount points, not the LVs.  When I look at disk utility, it shows them as separate peripheral devices (i.e., hard disks) that are unpartitioned.  So I think we've skinned the cat two different ways, anyway.

Also, now that you mention it, I think I discovered the reboot trick after setting up LVM by accident as well.  I'm not very good at keeping track of how I get things done; much more likely to keep at it by trial and error till it works, which is great until I have to redo it for whatever reason that I failed to foresee.

Also, I got the postfix config options and the server options as well.  Perhaps whoever wrote the setup program assumed that anyone who would set up encrypted LVM RAID must be setting up a server.

Glad it's working for you now!

---

### Post by tonywhelan on 2010-10-22
[QUOTE=Karl1982;9245874]Well, I finally fixed it, although I still can't quite explain the problem.  You won't believe what it came down to.....
/QUOTE]

Glad you got it working, BUT can I ask you if you actually tested the RAID by booting with one disk only?  

I can build an encrypted RAID 1 array with 10.04 without any errors, using the standard process you first used; but if I then boot with just one disk (either) the system never prompts for my encryption passphrase so it goes nowhere(though I have set the system as boot degraded = TRUE, so it should boot).

I had originally given up on Ubuntu for RAID, and tried Centos 5.5 which was easy to set up and it booted fine with just 1 disk. But CentOS doesn't support the network card chip in my machine, and trying to work around that was a nightmare.

Your earlier observation about lack of support for encrypted RAID is still true, I've found nothing so far that explains this. :(

---

### Post by tonywhelan on 2010-10-22
There are some active bugs about this:
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/488317](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/488317)
[https://bugs.launchpad.net/ubuntu/+s...up/+bug/251164](https://bugs.launchpad.net/ubuntu/+s...up/+bug/251164)

But they don't seem to be getting much attention, so don't hold your breath.

---

