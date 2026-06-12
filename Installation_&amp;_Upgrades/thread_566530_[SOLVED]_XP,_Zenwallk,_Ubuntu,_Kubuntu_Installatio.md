---
title: "[SOLVED] XP, Zenwallk, Ubuntu, Kubuntu: Installation order"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by Mr_JMM on 2007-10-03
Hi,

I'm starting kinda from scratch and want to install XP (pro), Zenwalk, Ubuntu and Kubuntu. I have two HDD's but for the moment will try and get them all on one 250GB.

I have set up the following partitions using GParted via the install CD:
- 98GB (?) Primary, NTFS
- 140GB Extended
    - 20GB Logical, ext3 (Will be a linux OS)
    - 20GB Logical, ext3 (ditto)
    - 20GB Logical, ext3 (ditto)
    - 500MB linux-swap
    - 80GB Logical, ntfs (not sure. may split again...(I read somewhere about needing partions with "/" and "/home" but would ask for your advice there as well)

I won't to keep the Lilo grub but that's only because it's the one I got used to and have learned a bit about editing it etc.  What is the best order to do things?
XP Pro is already installed (I knew that much).

Also, if I later add more disto's (more than likely will be on a different HDD) does that alter what i do now?

And (sorry), If I did want to learn and play with other grub ... things, is there an easy way to  switch?

As always, many thanks in advance,

Cheers,

James

PS I did a search and went through 9 pages (yes, honestly) but they were all slightly different situations and/or the advice was over my head a bit. Be gentle :roll:

---

### Post by maybeway36 on 2007-10-03
I would say to install XP first, then all your linux distros, making sure to end with one of the Ubuntu installations, because it can detect pretty much every other OS and add it to its boot menu.

---

### Post by Mr_JMM on 2007-10-03
Thank you.

XP is already installed. If I install Ubuntu last, how do I set it so I use the Zenwwalk Lilo grub (I think I mean "grub". The thing that lets me choose the OS)?

---

### Post by kellemes on 2007-10-03
Ubuntu will not detect other distro's, not my experience..

Install XP first.
Install one of the distro's you want to manage the bootmanager from (assuming this is *buntu it uses Grub as bootmanager), instal distro-2.. if it is using Grub as a bootloader.. let it install Grub and fix the Grub-install you had from dist-1 with [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").. this leaves you having a bootloader not knowing about dist-2.. you can fix this by pointing to the /boot/grub/menu.lst of dist-2 (configfile=(hd*,*)/boot/grub/menu.lst ((hd*,*)  should point to /boot partition of dist-2)
so again, you create a nested bootmenu by pointing to it's menu.lst like so..
title        MySecondDistro
configfile   (hd*,*)/boot/grub/menu.lst

If dist-2 (or dist-3) uses Lilo.. let it install Lilo in /-partition (not MBR)..by the way, Zenwalk will give you this option.. then you can chainload dist-3 like so..
title        Zenwalk
root        (hd*,*) .. should point to /-partition
chainloader    +1


Edit:
For all this info and more see.. [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by kellemes on 2007-10-03
By the way, I haven't studied your partition-scheme..
But this is how I have it setup using ArchLinux, Zenwalk and Windows..

- Windows on first partition of bootdisk. (needs to be first always)

- Dist-1 (using Grub) has..
swap-partition (2x memory with max of 2G)
/var-partition (don't remember how large) reiserFS (you don't need this if you don't want it)
/boot-partition (500K) ext2
/-partition (10G) ext3
/home-partition (20G) ext3

- Dist-2 (using Lilo.. remember the chainloading?)
uses the same swappartition as dist-1
has it's own /boot-partition
has it's own /-partition
has it's own /home-partition.

So the only partition to share is SWAP.
Don't let you talk into sharing /home.. this can only give you crap!
And remember.. to use this setup **every dist** needs it's own boot-partition.

---

### Post by Mr_JMM on 2007-10-03
What's the difference between /-partition and /home-partion?

I read a thread were someone was be-littled because he had 15 partitions. Following your advice and taking in to account I'll have 4 OS's on one hard drive, that's :-

1 XP
1 Swap
3 each per Linux distro (boot, /-part and /home-part)

that's 11 partitions

If I read other advice correctly it'll be:
- Primary partition NTFS 98GB XP (pro)
- linux-swap partition 2GB
- Extended partition 90.2GB*
  - (Ubuntu)
    - boot partition ext2 500MB
    - /-partition ext3(?) 10GB
    - /home-partition ext3 (?) 20GB
  - (Kubuntu)
    - boot
    - /-part.
    - /home-part.
  - (Zenwalk)
    - boot
    - /-part.
    - /home-part.

Is this correct? I assume it's all wrapped in extended partitions due to a max. number being allowed or have I mis-understood that?

Many thanks.

---

### Post by Mr_JMM on 2007-10-03
Ok. Set up all the partitions in advance as per above but I now have another question: How do you install Ubuntu and tell it which partition to use for each area (swap, boot, home etc.)? I get the list of all the partitions but Ubuntu seems to want to re-partition things and it won't let me se;ect the swap partition? I am in the screen after selecting "Manual" for Prepare Disk Space.

Many thanks.

---

### Post by Mr_JMM on 2007-10-04
Sorry for this but I've now been trying to sort this out for over 12 hours!

...


[SIZE="1"]bump[/SIZE]

---

### Post by Mr_JMM on 2007-10-04
Ok. I'll ask a different question as I think I may have seen my error.

Is it better to create say a 30GB partition and leave it at that, then when installing Ubuntu let Ubuntu divide up the 30GB partition instead of doing it all in advance and trying to "point" Ubuntu at everything?

Many thanks.

---

### Post by Mr_JMM on 2007-10-04
[FONT="Tahoma"][COLOR="Blue"]To quote Janice from Friends (My fiancee watches it, shush) "Oh My God!"

Success. Not just success but wow. It all works. More than just works, it's f'ing awsome.

Ok, that's enough gushing, how'd I sort it?

I went back and set up all the partitions using a stand alone version of GParted (created a dedicated CD). XP was already installed. The problem I was having before was not knowing how to "point" the partition manager at the partitions I created. Part of this was due to the fact that the GParted dedictaed program doesn't give the option of how to mount the partitions I created. After a lot of "wtf's?" I used a another piece of advice I found on this forum which went along the lines of "You only live once... just get on with it" or something. I did just that.

From the "Prepare Disk Space" screen I selected "Manual" -> At the list of Disks and partitions I ticked the ones I wanted to use which sets it to format these (this step may not have been necessary) and then highlighted those partitions (after writing down which sdxy went with which partition) and clicked "Edit". Here I was given the option of how to mount them. D'Oh!

After that it was just a case of going through all the steps.

The first time it restarted it failed. I didn't catch what failed but it restarted itself and booted no problem. Grub came up and showed XP, Vista, Zenwalk and the various Ubuntu options. All loaded perfectly.

Back to booting Ubuntu, it all went faultlessly, desktop came up and it had ALREADY DETECTED MY NETWORK and had checked for updates. Now that was impressive. Had a moments panic when I got a blank screen before realising it was just gone to screensaver!!!

Updates all downloaded and installed.

Well! What can I say. I'm not getting rid of XP and Vista; At least not yet, BUT I am converted. Ubuntu certainly deserves the reputation it has.

Thank you everyone. Thank you.[/COLOR][/FONT]

=D>=D>=D>=D>=D>

:guitar::guitar::guitar:

PS: yes, I know I'm supposed to use black text but I wanted this post highlighted!

PPS: Nearly forgot. To answer the thread titles question: Install XP -> Zenwalk -> Ubuntu for default Grup loader, XP -> Ubuntu -> Zenwalk for Lilo (my prefered choice) loader. Both options tried and tested.

---

### Post by kellemes on 2007-10-04
Sorry it took so long.. I had to go work the last many many hours.. :(

Do I understand it all went fine?
Or do you have more questions?

---

### Post by Mr_JMM on 2007-10-04
[quote=kellemes]Do I understand it all went fine?
Or do you have more questions?[/quote]

It *worked* out fine in the end. At this stage, as far as installation is concerned then no, I have no more questions.

Thank you kellemes, it was your last post that, once I just got on and did it, that made everything work. Big grins to you.

Cheers.

James

---

### Post by kellemes on 2007-10-04
Good job!
If you have more questions just let me know..

---

