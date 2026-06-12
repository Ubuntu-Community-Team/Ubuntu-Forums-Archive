---
title: "How to use single SSD as main drive and RAID for data?"
date: 2017-04-22
forum: Installation &amp; Upgrades
---

### Post by hihp2 on 2017-04-22
I have a new system put together with a single 120 GB SSD and two 1 TB HDDs on which I intend to install Ubuntu Server 16.04 LTS. I want to run a web server, mail server, samba file server, media server and some other stuff on it. 

I would like to use the SSD for the actual OS stuff, i.e. booting etc. The HDDs I want to put into a RAID1 and use for data. (Not sure yet what backup solution I will choose, but yes, I am aware that a RAID1 is not a backup solution.) 

Unfortunately, searching for this did not bring up much. All how-tos for RAID1 feature only two drives and set up a swap RAID and then another RAID for the root partition (I shall call the latter the "main RAID" from here.)

So my question basically is: what kind of partitions do I need to set up? 

Initially I thought I would just use the SSD as root and then add a swap RAID and the main RAID for the data, but my knowledge of Linux appears to be insufficient... 

Should I even bother using the HDDs for swapping, or should I rather create a /swap partition on the SSD? 

Do I indeed put the root partition on the SSD, or what should I put there? 

My issue is: I think for a server, I will definitely want to have /var on the main RAID, correct? But probably, /home and /srv should be there, too. However, I do not want to create three different partitions there because then I would have to limit them in size, and I really do not know which of them should be which size, etc. 

Or can I declare both the SSD and the main RAID to be the root partition?

---

### Post by TheFu on 2017-04-22
too. many. questions. too. answer.

There are many things you CAN do.
There are a few things you SHOULD do.

I would put /var on the SSD, so the logs get the performance you want. 
i would put all the web files on the RAID somewhere.  DB files, web files, etc. do not HAVE to be under /var/.  You can put them anywhere you like.

You can make a single partition for both 1TB disks, then RAID on that, then LVM over that, then VGs and LVs on those disks. That way, you can resize the different LVs /var/www, /home/, and whatever else you want sized as needed on the RAID'd 1TB.  LVM lets you resize LVs without screwing around with partitions.  LVM does some good things for performance too.

Use mdadm for the RAID stuff.
Treat LVs like partitions. That's the easy way to think about them.  Put the file system onto the LV.

I'd keep the swap on the SSD too, assuming you want any swap at all. For servers, I try to tune the workload and RAM so that no swap is needed. Makes life easier.

BTW, you didn't ask any questions about security. Certain things you are proposing I would never do. I'd never mix low security and high security processing on the same system.  email is extremely dangerous.  It should be on a standalone system.  Samba is an extremely low security tool. I'd have it nowhere near the dangerous email stuff.

Make sense?

---

### Post by hihp2 on 2017-04-22
Okay, so let's set aside /var... Obviously, you are right, when I install LAMP, I should just set it up so that it uses whatever I put on the RAID. Needs a bit more tinkering, I guess, but that way I learn more. 

Regarding swap: since I have 8 GB of RAM and my system probably won't need that much RAM anyway, let's also put that aside for a minute. I think for the time being I'll put that on the HDDs, but I'll leave quite some unassigned space on the SDD (as contingency/overprovisioning space), so I can always do that later.

So the main point is here, and please bear with me for having been a computer user for twenty years, but under Windows, so my Linux knowledge is limited:

As far as I understand you, I would made the SSD a physical volume, then put a RAID on the HDDs as a physical volume for a logical volume to be set up using LVM? 

And then? I don't know much about LVM yet apart from the fact that it exists.. 

Btw, I dunno why, but I would kind of like to set this up during the server installation... Especially in case I at some point ruin the system so much I have to do this again. So I would like to do this using the partitioning options presented during the installation process... 

Finally, on security: This is all for personal use, only. I want to set this up as my home server, and regarding e-mail I want to set up some sort of Exchange-compatible software (Zarafa or something like that), which I will then use to connect my Android phone to so I can remove my contacts and calendar off Google. (I have my main email account somewhere else, and the idea is to poll all email from it and keep it only locally.) So security is not of much concern at the moment since the number of users will be limited to me, basically.

---

### Post by hihp2 on 2017-04-22
Okay, I did read up a lot, and thought a bit (or maybe the other way round). Here is what I came up with, and I would be glad if you could let me know your thoughts:

SDD:
- one /boot partition, fairly sized (4 GB) - should last forever, and will ensure the boot stuff is on the SDD
- one main partition, about 90 GB of size. Will be mounted as / 

HDDS:
- each gets two partitions, one with 16 GB and one with the rest of the space
- on each pair of partitions, I will set up a RAID1
- the smaller RAID1 will be used as swap
- the larger RAID1 will be used as the physical volume for LVM

LVM:
- will be used to get future flexibility
- so far, only one volume group and in this, only one logical volume will be set up
- the logical volume will be about 500 GB in size (to have the rest as contingency)
- the logical volume will be mounted as /srv

My idea here is: I am free to set the system up the way I want, so I will make sure that all the directories that contain the large files will sit under /srv, especially the files for the samba shares (which will also be used by the media server, partially, etc.). In the future, I will then set up some backup strategy where I separately back up /srv and the rest of the system.

If all else fails, and at some point I e.g. want to move /var to the hard drive RAID, I can always create a directory /srv/var and then then mount that as /var, right?

---

### Post by oldfred on 2017-04-22
I do not know RAID, LVM or servers. So if anything I post conflicts with suggestions from TheFu follow his advice. 

But you are just doing a standard install to SSD. So I would not even install swap into RAID. The new 17.04 will eliminate swap partition and use swap file. But if server you should be installing 16.04 LTS until 18.04 comes out.

Almost all RAID or LVM installs I have seen, do have separate /boot partitions outside the RAID or LVM. But they have / inside LVM.
If full install to SSD, I would just have / (root) as one large partition. Then you do not have to worry about size of /boot & size of /.

Is system UEFI or BIOS?
If UEFI you need extra partitions.

Even if BIOS you can use gpt,  but then need bios_grub partition.

TheFu did not refer to his site. You need to review it.
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

Use of server is command line. I think it was TheFu that suggests you only use command  line.
But that has a steep learning curve.
You do not need to install desktop, but some beginners (like me) with servers may want a gui. 
Desktop install includes all the standard desktop software which you do not want nor need. But you can just add the gui.
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Some others have posted these.
Lightweight Desktop environment
Ubuntu Server + lxde
works smooth in under 256mb ram on a p2
sudo apt-get install lxde
Or Xfce GUI without any of the associated Xubuntu applications
sudo apt-get install xfce
Comparison of desktop environments 
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
Minimal gnome
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback

---

### Post by TheFu on 2017-04-23
If you don't use LVM, I don't think my recommendations are probably what you want.  LVM is at the center of all my physical systems for many, many, reasons. It is a chief reason why Linux is extremely flexible. LVM is critical to backups too.

I have never done a "LAMP" install.  I always start with a simple, base, system that has ssh and nothing else, then add what I want using devops methods. In the old days, I used scripting.  Being consistent is important. Letting some installer control your base is a bad idea, IMHO.

Any directory can be a mount point.  /srv or /var/www/html ... depth doesn't matter. It would be best if the directory were empty, but even that is not required.  99.99% of people want empty directories as mount points. There are reasons to mount over an existing directory, however.

All email is dangerous. Been running email servers for a few decades. It has never been more dangerous than it is today. Separate system. Definitely.  Compartmentalization is a key advantage that Unix provides over the other options. Use it.

Why put the swap on RAID?  If you do that, are you using ECC RAM too?
Why have more than 1 partition on the RAID?  With LVM, you only need 1 partition per physical disk.  Ok, that isn't true. You can have zero partitions, but that is a bad idea, IMHO.

Please reconsider your LVM decision.

---

