---
title: "Multi-boot 3 buntu's"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Naazir on 2007-09-25
I'm working on setting up a multi-boot system. I have 2 hard drives I'd like to use. I've installed/played with Ubuntu / Kubuntu and Xubuntu already in an attempt to move past Microsoft OS's, not quite there yet but so VERY close!

I would like to set up the / for each os in a separate partition on the first hard drive, create a shared /swap at the beginning of the second hard drive and use the remainder of the second hard drive as shared space, preferably the /home folder for the user account I will be using.

Here's some basic info before I start prattling on and on here.
hard drive 1 will be sda
hard drive 2 will be sdb
user account will me *name*

From what I know so far about Linux and the resources available to me at the moment, I *think* I would like things set up like this:

sda1 would be / for Ubuntu
sda2 would be / for Kubuntu
sda3 would be / for Xubuntu

sdb1 would be /swap (shared)
sdb2 would be /home

I was going to use the same user account and machine name for each installation. I thought this would create a /home/*name* that I could access from any of the 3 'buntu's but I was mistaken. I was unable to boot into previous 'buntu's because the /home/*name* folder was no longer accessable.

I started hunting around online for answers/suggestions and came across someone mentioning using the storage space as /home/*shared* instead. I tried that with 2 'buntu's but only the second one I installed could see the *shared* folder, though only root could access it. I changed the permissions but this didn't help as that whole mount point (/home/*shared*) didn't show up in the 1st installed 'buntu (Ubuntu).

(takes a deep breath...)

So, hopefully someone understands what I'm trying to accomplish and can help me out. I'm wondering if I need to set the storage partition as /home and then maybe create a *shared* folder in it that can be accessed from each 'buntu? Reading everything I'm digging through for answers has caused my brain to swell and throb. Seemed like a good time to just jump in here and ask some experts!  :biggrin:

---

### Post by rsambuca on 2007-09-25
> **Naazir said:**
> I'm working on setting up a multi-boot system. I have 2 hard drives I'd like to use. I've installed/played with Ubuntu / Kubuntu and Xubuntu already in an attempt to move past Microsoft OS's, not quite there yet but so VERY close!

I would like to set up the / for each os in a separate partition on the first hard drive, create a shared /swap at the beginning of the second hard drive and use the remainder of the second hard drive as shared space, preferably the /home folder for the user account I will be using.

Here's some basic info before I start prattling on and on here.
hard drive 1 will be sda
hard drive 2 will be sdb
user account will me *name*

From what I know so far about Linux and the resources available to me at the moment, I *think* I would like things set up like this:

sda1 would be / for Ubuntu
sda[COLOR="Red"]**2**[/COLOR] would be / for Kubuntu
sda[COLOR="Red"]**3**[/COLOR] would be / for Xubuntu

sdb1 would be /swap (shared)
sd[COLOR="Red"]**b2**[/COLOR] would be /home

I was going to use the same user account and machine name for each installation. I thought this would create a /home/*name* that I could access from any of the 3 'buntu's but I was mistaken. I was unable to boot into previous 'buntu's because the /home/*name* folder was no longer accessable.

I started hunting around online for answers/suggestions and came across someone mentioning using the storage space as /home/*shared* instead. I tried that with 2 'buntu's but only the second one I installed could see the *shared* folder, though only root could access it. I changed the permissions but this didn't help as that whole mount point (/home/*shared*) didn't show up in the 1st installed 'buntu (Ubuntu).

(takes a deep breath...)

So, hopefully someone understands what I'm trying to accomplish and can help me out. I'm wondering if I need to set the storage partition as /home and then maybe create a *shared* folder in it that can be accessed from each 'buntu? Reading everything I'm digging through for answers has caused my brain to swell and throb. Seemed like a good time to just jump in here and ask some experts!  :biggrin:
You need to make the following changes above.

---

### Post by Naazir on 2007-09-26
I guess this was a tougher one that I thought??

---

### Post by LaRoza on 2007-09-26
You should use GParted to set up the partitions, then do a text install, giving the appropriate mountpoints for each directory.

I have gotten 12 OS's, including XP, working together on ONE hard drive at ONCE.

---

### Post by Naazir on 2007-09-26
> **LaRoza said:**
> You should use GParted to set up the partitions, then do a text install, giving the appropriate mountpoints for each directory.

I have gotten 12 OS's, including XP, working together on ONE hard drive at ONCE.

I can get all 3 'buntu's installed and running, my problem is trying to get all 3 to use the same account and same /home/*name* mount point. 

I'm beginning to think Linux can't do what I'm asking.  :(

---

### Post by rsambuca on 2007-09-26
If you have already installed the three distros, all you have to do is edit your /etc/fstab to mount the same /home partition.

---

### Post by LaRoza on 2007-09-26
You can install them all at once, in Ubuntu:

```

sudo aptitude install kubuntu-desktop

```

```

sudo aptitude install xubuntu-desktop

```

When you log on, you can choose which session to use. Simpler than a multiboot.

---

### Post by Naazir on 2007-09-26
> **rsambuca said:**
> If you have already installed the three distros, all you have to do is edit your /etc/fstab to mount the same /home partition.

hmm... well I took a look at the /etc/fstab file... I'll do a little research and make sure I get it edited correctly. Actually, I'm going to reinstall the first 2 OS's again so I can get it back to the way I want them then I'll edit that file and see if I can't get them all to map /home/*name* to the same place on the same drive. Thanks for the tip!

I'd prefer to install all 3 individually. This is more of a learning process for me than building a working system. I've worked with multi-boot setups before (my home pc runs XP and Ubuntu) but this one's just a tad trickier.  ;)  I'll post back here after the next couple of installs to let you know how it's going.

---

### Post by rsambuca on 2007-09-26
Hold on a sec.  If you are going to install them again separately, then you do not have to edit the fstab as the installer will set everything up.  When going through the installation process, just make sure you point the /home partition to the one you have designated, but don't format it.

---

### Post by Naazir on 2007-09-26
> **rsambuca said:**
> Hold on a sec.  If you are going to install them again separately, then you do not have to edit the fstab as the installer will set everything up.  When going through the installation process, just make sure you point the /home partition to the one you have designated, but don't format it.


I've done that but one or the other OS will not have access to the /home/*name* folder.

---

### Post by rsambuca on 2007-09-26
OK, you are not installing them properly, but don't worry.  We should just be able to edit each fstab separately.  Post your /etc/fstab files from each distro and we can figure it out.

---

### Post by Naazir on 2007-09-27
> **rsambuca said:**
> OK, you are not installing them properly, but don't worry.  We should just be able to edit each fstab separately.  Post your /etc/fstab files from each distro and we can figure it out.

Didn't see this till after beginning my reinstalls. No worries. If it's possible, I'd like to have all 3 'buntu's map /home/*name* to the second drive like I originally planned anyway and the last time I installed them I had done something different. 

I'm putting Ubuntu on right now. I wiped out both hard drives and only created the partitions I needed for this first OS. There's an /sda1 on drive 1 for root (1/3 the total hard drive), a /swap on drive 2 (4GB) and the remainder of drive 2 is partitioned as /home.

Drive 1
/sda1  -  Ubuntu's /
free space

Drive 2
/swap  -  will be shared for all 3 'buntu's
/home  -  remaining space on the drive, also hopefully shared

So, from what I've heard here so far, when I install Kubuntu next I should create the second partition on Drive 1 and format it, leave the /swap partition alone and set the 2nd partition on Drive 2 as /home again but don't format it? I'm sure I did that before but I'm more than happy to do that again. 

I'll wait for someone's go-ahead before beginning the Kubuntu install.

---

### Post by Pumalite on 2007-09-27
4 GB of /swap is a waste. I GB is more than enough.

---

### Post by Naazir on 2007-09-27
> **Pumalite said:**
> 4 GB of /swap is a waste. I GB is more than enough.

Is it *bad* or just unnecessary? I had 2 drives in the computer and thought putting the swap on the second drive would help the system run smooth/faster. And since it was an 80GB drive I thought why the heck not give this machine plenty of swap space!  :)

But... if it's *bad*, could slow the system, or in some way is NOT quite as good as I thought it would be, I can certainly change it.

---

### Post by Pumalite on 2007-09-27
In my experience /swap is almost never used. If you have 1 GB of memory, you'll probably be fine with 500 MB of /swap. Unless you transcode HUGE movies.

---

### Post by PmDematagoda on 2007-09-27
If you want to use Ubuntu,Kubuntu and Xubuntu, why don't you install the desktop environments onto just one installation? It is easier, uses less space, but one negative is that your main menu gets cluttered, but that can be easily organised.

Install KDE on Ubuntu with:-


```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

Install Xfce on Ubuntu with:-

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

If you want to install Gnome on Kubuntu or Xubuntu:-

```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

You can find all the information you need in Psychocats. A very useful website.:)

---

### Post by Naazir on 2007-09-27
> **PmDematagoda said:**
> If you want to use Ubuntu,Kubuntu and Xubuntu, why don't you install the desktop environments onto just one installation? It is easier, uses less space...

Well, the versions themselves are slightly different. Meaning, they come with different apps as well as interfaces. It's not just the interface I want to change, I want to play around with all 3 'buntus. I also want to play around with multi-booting. Putting all 3 on one computer made a good fit for that.  :cool:

I've played around a little with a bunch of other distros and found I like the 'buntu's the best. Especially since Feisty. Remember, this is just a practice, learning, experimental computer. Honestly, I was in the process of creating a bootable USB flash drive with a fully functional OS (Unlike a Live CD, this bootable USB drive can be used, updated, changed and retain all of it) and wanted a clean install of Xubuntu because it was reportedly smaller/faster. Then I decided to make 3 bootable USB drives since I like the interface of Kubuntu better.... you can see how I ended up here right?  :-k

[Xubuntublog's bootable USB drive link]("http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/")


And thanks for the Psycocats link, checking it out now.

---

### Post by PmDematagoda on 2007-09-27
You do get the Apps as well when you install the Desktop Environments, that's what I meant by one of the negatives being the cluttered Main menu with the apps of Gnome, KDE and Xfce all together.:)

---

### Post by Naazir on 2007-09-27
Ahhh... I've installed KDE on ubuntu before and all it did was change the look. The underlying OS was the same. I guess this is different. It sounds like learning "sessions" is next in line after i get the 3 OS's working the way I want and then I make my bootable USB drives!

---

### Post by Naazir on 2007-09-27
Ok, waited long enough. Going to install Kubuntu now. I'm going to create a second partition on Drive 1 (sda2) for root, I'll use the existing /swap and I'll also point /home to the same location I used for Ubuntu (2nd hard drive, 2nd partition). I'll post back when it's done with results.

(And I'll only format Kubuntu's root, nothing else)

---

### Post by danbh on 2007-09-27
I've been playing with this also.  The only tricky thing is permissions.  
Most settings are stored in files under the /home folder, so that is simple, but the permissions of the home folder is a little more tricky.  For example, the permissions are organized by number, NOT by name; even though when you run ls -al it lists the permissions with names.  For example, the root user is of UID 1000.  So sharing accounts across installations looks a little tricky to me.  I think you need to get the UIDs matched, which looks can be done under System > Administration > Users and Groups.  I don't know how to do that from the command line.  

If you are curious how to move the /home to a different partition (ie you already installed and forgot to have /home mounted where you wanted), you can check out my personal website for my experience at:
hollocher.is-a-geek.com / drupal /?q=node/39
(remove the spaces)

This website is running off of my personal computer, and as such, goes down whenever I turn my computer off, which is at least nightly.

---

### Post by Naazir on 2007-09-27
> **rsambuca said:**
> Hold on a sec.  If you are going to install them again separately, then you do not have to edit the fstab as the installer will set everything up.  When going through the installation process, just make sure you point the /home partition to the one you have designated, but don't format it.

> **Naazir said:**
> I've done that but one or the other OS will not have access to the /home/*name* folder.

SUCCESS!!!

It would seem I was mistaken earlier when I thought I had tried installing a second 'buntu and NOT formatting the /home mount point. I tried it again today, Ubuntu then Kubuntu, without formatting /home on the second hard drive. Logging into either OS works fine and the account I use to log in has read/write access to the home folder. I even created a sample file from one OS then rebooted into the other to delete it and it worked! 

Currently I am installing Xubuntu the same way but I have a feeling this too will work fine. I'll pretty up the GRUB menu some to make selection easier too. VERY happy camper here! Thanks for the help!

---

