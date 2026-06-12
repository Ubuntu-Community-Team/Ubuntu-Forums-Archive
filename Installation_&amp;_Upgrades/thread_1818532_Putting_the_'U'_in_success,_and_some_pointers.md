---
title: "Putting the 'U' in success, and some pointers"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2011-08-04
After a needlessly arduous process installing Ubuntu onto a pc, I have another question. I had two HDD's in this pc. A 150gb and 80gb, XP is operating on the larger of the two, the smaller has been completed formatted with Ubuntu 11.04 on it. Before I put the case back together for good, what is the preferred drive setup, xp as master or vice versa? I plan to hopefully use Ubuntu as my primary OS as I learn. The XP contains a lot of old files, mainly media.

Any guidance on how to set myself up? Applications, programs, preferences, etc? I mainly will use the pc for media, internetting, and some word processing.

Now, for a few pointers to anyone who will listen:

Read directions thoroughly, the answers are often simpler than you think.

And try the alternate version of Ubuntu's live cd for an install or different media if you are having difficulty installing.

Thanks:popcorn:

---

### Post by Basher101 on 2011-08-04
Hello bradlees,
For your first question, Windows is a dominant OS, in other words it "thinks" it is the only OS on the Hard drive. Its always important to first install windows and afterwards Linux. So Windows should be your Master.
Second, setting yourself up. I suggest you keep Ubuntu on a small partition where you keep the system files and programs only. Other files, espacially large files should be kept on another partition. Why do this? Because i had really good expirience with the Backup-tool Remastersys, it backs up everything for you into an iso file. I messed up a few times with linux in the first weeks and was happy to have a USB to fall back on and not fear trying things with linux. The only limitation is the iso must be less than 4GB. I dont know the maximum size it can back up, but i was able to back up my 10GB big linux system with all files. For other programs i would recommend you to search restricted extras for ubuntu in the software center. It contains codecs, flash and other things that did not come with ubuntu preinstalled. For your media the preinstalled Video player should be enough, but if it does not suit you install Amarok. Its similar to iTunes. That should be it to set you up firstly. If you want other recommendations feel free to ask :)
note: i am not familiar with doing posts so sorry if my post is a little hard to read, i have no expirience formatting my text> 

---

### Post by IWantFroyo on 2011-08-04
Which one do you want to automatically boot to? Ubuntu or XP? Make that one the master. You can boot into the other by changing your BIOS settings.

As for app recommendations, here are my favorite:
1) Firefox and Thunderbird for Internetting (Browsing, email, and RSS).
2) I prefer Abiword for my word processing needs.
3) Get the ubuntu-restricted-extras package. It has flash and some MS fonts. You'll probably want flash for your Internetting.

PS- Nice avatar, Basher101. I LOL'd. It isn't every day you see an Urahara penguin.

---

### Post by Basher101 on 2011-08-04
Bleach ftw xD back to topic:
also for interneting i would recommend Clipgrab, its like the Youtube to Mp3 converter for windows, only it has more options to it. To install it you need to: (sry i do not know how to put this in a code box...i will make sure to google it <.<)

sudo add-apt-repository ppa:clipgrab-team/ppa

sudo apt-get update

sudo apt-get install clipgrab

---

### Post by bradlees on 2011-08-04
I appreciate the help. I have an entire 80gb hdd dedicated to ubuntu. What do you suggest as far as partitioning this? I may have jumped the gun, I still haven't got this fully up and running on my pc. I have had the damndest time installing ubuntu or any distro altogether. I have tried a number of things and this alternate cd seemed almost to work.

Once I get this up and running I would like to have a rescue tool. A USB tool would be great.

---

### Post by bradlees on 2011-08-04
If I get this going, I;m definitely going to look into your suggestions.

I have tried unsuccessfully to load

Ubunut 11.04
Ubuntu 10.10
wubi
Mint
Xbuntu
Lubuntu

all on live cds or through a USB boot tool. The pc is older, but at one point, on this mobo and processor, maybe a different hdd, I had ubuntu installed and had no issues.
I'm hoping this succeeds

---

### Post by IWantFroyo on 2011-08-04
Yep, Bleach wins.

Okay. You don't need to do manual partitioning. If you have a dedicated HD, you can just have it use the entire disc.

I also wanted to suggest XChat IRC. How people live without IRC, I will never know...

As for your installation problems, you might want to give Ubuntu 10.04 LTS a try, and freshen the programs up with a PPA or two.

As for a rescue tool, I'm not sure. It's a good idea to have a bootable USB of Ubuntu or KNOPPIX so you can get your work off of your computer if it fails, but other than that, I don't know anything.

---

### Post by Basher101 on 2011-08-04
I have tried a few rescue tools and commands, but only Remastersys really did its job perfectly. The created iso is bootable, thus you have a portable, standalone Live CD (or usb) of your distro with all programs installed and configured. Saves alooot of time if you should mess up and are forced to do a reainstall...it takes ages to get all your programs back and configuring everything again.

---

### Post by bradlees on 2011-08-04
Its taking me forever just to get thing installed. 

I have a android phone, using froyo right now. If you have a phone, do you use anything in that regard?

---

### Post by Basher101 on 2011-08-04
Sry pal, my phone can't even access the internet...its just a basic mobile phone. Never had a Smartphone or similar.

---

### Post by bradlees on 2011-08-04
oh man, I regret to say I couldn't live without it. A few years ago, the thought would have never crossed my mind. they really are amazing devices nowadays.

---

