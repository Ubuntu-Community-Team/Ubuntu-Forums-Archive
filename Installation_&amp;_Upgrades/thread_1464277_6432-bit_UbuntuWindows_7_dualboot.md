---
title: "64/32-bit Ubuntu/Windows 7 dualboot"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Atreus10 on 2010-04-28
Well, okay, then.  Might as well explain my situation.

I have two computers at hand, my old, crumbling (but still pretty  mighty) desktop and a sleek (but rather bland) laptop, both with Windows  7.  I've been running various Linux distros in VirtualBox on both  machines for... psh, a year now?  Main distros have been Ubuntu, Fedora  (<3 Fedora) and SliTaz.  I started messing with linux mainly just to  play around with it and partly for the slight amount of geek-cred  >.>

So, anyways, last sunday night I decided to clear out a 50gb partition  using the Shrink Volume thingymabob on Win7 on my desktop and install  64-bit netinst Fedora on it.  Installing went well and after a few  tedious hours fiddling with the MBR and grub and windows bootloaders, i  got it up and running perfectly.  EasyBCD ftw.

Well, not perfectly... both systems have been acting up ever since...   But that's for a Fedora forum, not here.  (  [http://atreus.pastebin.com/yv7aEbf6](http://atreus.pastebin.com/yv7aEbf6) if you're curious.  got that error  repeated when trying to start rhythmbox from terminal since the shortcut  on the desktop didn't work)

ANYWAYS.  I'm thinking of clearing another 50 gig partition out of my  laptop and installing 10.04 on it.  So here's where the forums come in.

I'm paranoid when making major changes like this to my computer.  I  mean, majorly paranoid.  I even tried, before i tried dualbooting in  real life, dualbooting an old non-OEM copy of XP and Fedora in  Virtualbox (is that even legal, running Windows in vbox?  if it isn't,  forget i said anything >.> ).  The results...  to be honest, the  results were disastrous.  The fact that both fedora and win7 work on  this desktop right now is a testament that i'm not completely hopeless,  though.

So, before I install Ubuntu as a dual-boot on my (64-bit compatible)  laptop, i have a few issues to smooth out:

1.  64-bit or 32-bit?  I've had a lot of trouble with 64-bit, and yet,  it's 64-bit and can take advantage of all 4 gigs of my computers RAM.   (wwwwell, 3.75.  still more than 3.3 gigs)  I'm not asking what's the  difference, as I'm pretty familiar with it, I'm just asking the ubuntu  community as a whole which is more stable.  I'm going with LTS here as  i'd probably be too lazy to update it to 10.10 11.04 etc etc.

2.  Should i choose wubi?  I'm not keen on it as it installs it as a  file instead of a separate partition.  If not wubi, then I'd probably go  with 10.04 standard installation.

3.  grub or windows bootloader?  i don't really care, but windows is a  finicky OS, and i would rather have it control the boot.  if so, how?   [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) doesn't help too much  in that respect.  It's rather crappy, to be honest, more or less  glancing over the bootloader decision.  When i installed fedora i  installed grub on the fedora partition (i swear i did >:( ) but i had  to fight with bootrec on the win7 repair cd to fix it back up, because i  wanted a windows-controlled boot.  I found several different way to  have grub control it, and none of them were entirely too clear and none  of them agreed on exactly how to fix it.  also, is it true that the  ubuntu installer would detect windows and (CORRECTLY for god's sake, i  don't want to spend hours getting it fixed like the desktop) add it to  grub automatically?  if so, where is the option?  is it a window?  i'd  rather not much such an important option. D:

4. partitioning in the system.  would an LVM be okay?  i was thinking 4  or 6 gigs of swap, but what about other partitions?  Do i want a /boot  partition? on my fedora install i have a 350mb /boot partition and the  rest as an extended lvm partition containing 6 gigs of swap and a /  mounted ext4.  that was a setup i picked up from the various sites i  looked at while installing.  is that okay?

ah, any other questions i immediately have?  none that i can think of.   regardless of when this gets answered, i'm downloading the .torrent file  as soon as possible an lending my FiOS internet speed to the seeding  :)  how's that for payment, 1mb/s download from me? (course i'm going to  cap it at 1000kb/s, you think i'm insane? :P )

(this may have accidentally been posted by me already... CP shows nothing of the sort, though.  i must've logged out while typing this.)

---

### Post by zvacet on 2010-04-28
You can use 32 bit version and get all ram recognized if you install linux-image-generic-pae.You will find it in synaptic.

I think you don't need Wubi if you want to dual boot ( not install Ubuntu inside Windows).Install Ubuntu on separate partition using live CD.

For ram I think 4GB is enough.

Install grub on MBR and you don't need separate boot partition.Yes,grub will recognize Windows and add it.

---

### Post by Mark Phelps on 2010-04-28
> **Atreus10 said:**
> I'm paranoid when making major changes like this to my computer.  I  mean, majorly paranoid.  

Being "paranoid" means you have an unreasonable fear -- but given the risk of trashing your computer, you're not really "paranoid".

I would suggest that before you make anymore changes, you image off your Win7 install to an external drive.  You can do that using the Backup feature in Win7, or you can use a commercial product (Acronis True Image works well with win7), or you can use a free product like Macrium Reflect or EASUS Partition Master.

I would also suggest, if you haven't done this yet, to use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will come in very handy later if you need to repair the  Win7 boot loader.

Good Luck

---

### Post by kat3c on 2010-04-28
Don't use Wubi, I found it glitchy, and hard to uninstall.  Dual boot is the way to go.

Use grub, it'll recognize Windows 7/ntfs partition fine, the other way around is dicier....

I, like you, started playing around with Linux distros for fun and geekiness, on a laptop (ancient), and desktop (not ancient).  I've gone through many installs, reformats, even tried to triple boot Windows and two Linux distros (never got that working, gave up).  I arrived at partitioning a separate primary partition after Windows partition for the Linux distro, with logical partitions for root, swap (twice your RAM size, but whenever I check, seems like little is being used, not sure how vital a swap partition is) and home.  Just don't change/delete/add any partitions after you install, or Grub will not be able to find things as everything (partions) get renumbered.  I'm sure there's a way to modify some Grub file to tell it the new partition numbering, but I found it easier to reinstall.....

---

### Post by Atreus10 on 2010-04-28
zvacet:  oh, i can get all 4 gigs?  Sweet.  I'll probably get 32-bit, it'd probably be a bit more supported by packages, though i dunno.
And are you sure grub will recognize windows?  The fedora install didn't, correctly at least.  is it a checkbox option, or does a window pop up?  and does it correctly add the rootnoverify (or root) and makeactive options in grub.conf?  i got so bloody frustrated at fedora when the online install guide i used more or less failed and had didn't add anything to have windows boot correctly.

Mark Phelps:  technicality >.>  also, backup and recovery.  ah, long story there.
we got the laptop for dirt cheap off of.... was it HSN?  When i opened the box, i found three things: the computer, the power cord, and an instruction booklet.  no install/recovery cd or dvd at all.  Now, there was a program on my computer called Gateway Recovery Management (gateway being the computer manufacturer of course) that created 3 Factory Default DVDs and 1 driver/application DVD.  I'm not sure if that would be good enough, though, and i will take a look at the free programs you posted (we're kinda short on money right now).  Also, while installing fedora i found.... [these]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") which are win7 recovery center discs....  I have burned the CD.  would that work?

kat3c:  i don't have too much need for a separate /root partition.  sure it might be safer but to be honest i'm not doing too much "deep" stuff with linux.  i might turn it into a server, though, but that's unlikely and even then down the road a bit.  and, i was told to put swap in a separate partition.... don't ask me why, though.  i'll probably just end up with the same partitioning scheme on fedora as it seems to have worked (though there have been problems as noted in my first post).  and i probably won't edit them when i'm done, as this is a dual boot and i use windows normally on my laptop, as i play a lot of games ;)
and, as per the amoutn of swap, i heard a good piece of advice on the net while l was installing fedora.  if you're physical RAM is < 3 or 4 gigs, then the swap should be twice that.  if you have more than that, make it your RAM size + 2 gigs.

---

### Post by oldfred on 2010-04-29
I converted both my desktop and laptop (both about 3 yrs old) to 64 bit and have had no problems (that I can tell).  Karmic was the best install ever for me - both computers just worked, but I had done upgrades in place before and almost always some config or setting had to be changed to get it to work right.

I dual boot XP and if you are want to use data from both windows &  ubuntu create a shared NTFS partition for that shared data. I share my firefox profile, thunderbird profile & photos for picassa. I only try to read from my windows system partition even though it should be ok to write.

For Ubuntu, I would suggest only 10-20GB for / (root), swap equal to RAM if you want to hibernate, and the rest as /home. I have loaded many applications and used 5-6GB of root.

---

### Post by Atreus10 on 2010-04-30
Well, it works!  I downloaded both the i386 and the amd64 versions via bittorrent (both their ratios are a tad under 10 as of this writing :D ) and installed the amd64 version.  first thing i noticed was the fact that i could either install it on the free space i had (i had a 50gb partition free set aside for it) or integrate it and add the win7 loader to grub which would have installed it on the largest used partition, but not both, it seems.  as in, i couldn't add it to the free space AND have it add the other OS to the bootloader.  least, it didn't say i could.  that pissed me off as i wanted to add it to the free space while also adding windows to grub, which neither option immediately said it could do.  so i booted back into windows and unshrunk the partition, rebooted twice, and told it to use the option to put both other OSes into the bootloader, and told it to use 52.0 gb.  besides that, installation went well and both ubuntu AND win7 worked OUT OF THE BOX, which i have to give credit to you guys because that is downright OSSUM.
and, yes, just to check i DID boot into both windows and ubuntu.
so, it wasn't as complicated as i expected, which, like i said, kudos to the devs.
i'm still wondering why you guys don't use grub2 (i don't think, i think it said grub 1something8)...

---

