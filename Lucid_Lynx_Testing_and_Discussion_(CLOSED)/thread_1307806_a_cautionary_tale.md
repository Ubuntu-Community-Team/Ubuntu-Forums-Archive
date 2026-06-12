---
title: "a cautionary tale"
date: 2009-10-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-10-31
I did a fresh install of karmic from the destop release (64bit) . for upgrading to lucid . installed to an empty drive , partitioned as 30gb  / and 160gb /home , installed grub2 to the mbr of this drive ( I give each install it's own drive and let it install its grub (whatever version) to that drives mbr . When I set the bios boot order to boot this drive I get "GRUB loadingread Error" .
 I reset the boot order to boot my karmic original install and booted to that . then I cut and pasted the bootstanza from the "lucid" grub.cfg into the karmic grub.cfg as an extra entry to see what would happen . trying to boot that entry gives "you have to load the kernel first".
 taking a hint from Ranch hand's grub2 introduction in the karmic forum I added another minimal entry to my karmic grub.cfg (to make for easy editing)

as the karmic for lucid wrote the boot stanza 
```

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set c5e7f16b-8078-41b4-bf56-04c1963c5d6c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c5e7f16b-8078-41b4-bf56-04c1963c5d6c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
```  
the UUID is correct 

when I try to boot from the "lucid" drive it dosent even get to the menu it gives the "GRUB loadingread Error" 
when I add this stanza to my karmic grub.cfg and try to boot that entry it gives "you need to load the kernel first"
if I edit it the set root line to (hd0,1) it gives "cannot read the file"

the extra entry I added to my karmic grub.cfg 

```

 menuentry "lucid" {
        set root=(hd3,1)
        linux /vmlinuz root=/dev/sdd1 so 
        initrd /initrd.img
}
```

if I try to boot this entry it gives "you need to load the kernel first"
if I edit the set root line to read (hd0,1) it boots into "lucid" 


so beware if you have a multi drive multi boot setup you may have to stab around a bit to get it to boot . ubiquity (big supprise) seems to be getting the drives mixed up even though (this time) it got the uuid right .

---

### Post by Reiger on 2009-10-31
You may have more luck with ```
sudo update-grub2
```

---

### Post by ronacc on 2009-10-31
I was going to try that this evening , the problem in the first place was to get into the install at all since "lucid's" grub wouldn't even make it as far as the menu . by the time I solved that I had run out of time to play .

---

### Post by ronacc on 2009-11-01
this one is still running me in circles , begining to wonder if the boot sector on that drive isn't fubar . so far I have (from within the "lucid" install since I can boot it from my karmic menu" ) run update grub2  , no help . run grub-install /dev/sdd  , no help . run grub-install /dev/sdd1  , no help  . used install-mbr to installl a new mbr to sdd  rerun grub-install /dev/sdd  ,no help .  checked the partitions with fdisk -l   all showing correct for all drives . sdd1 is flagged "boot" ( shows that way in fdisk -l and gparted ) .

I think the clue is that even though sdd is hd3  I have to edit the set root line in the menu listing in karmic's grub.cfg to (hd0,1) to get "lucid" to boot  even though the linux /vmlinuz  line points at sdd1 .

is there a way to examine the mbr's directly ? I think grub-install is putting grub on the wrong drive .

---

### Post by lithorus on 2009-11-02
> **ronacc said:**
> this one is still running me in circles , begining to wonder if the boot sector on that drive isn't fubar . so far I have (from within the "lucid" install since I can boot it from my karmic menu" ) run update grub2  , no help . run grub-install /dev/sdd  , no help . run grub-install /dev/sdd1  , no help  . used install-mbr to installl a new mbr to sdd  rerun grub-install /dev/sdd  ,no help .  checked the partitions with fdisk -l   all showing correct for all drives . sdd1 is flagged "boot" ( shows that way in fdisk -l and gparted ) .

I think the clue is that even though sdd is hd3  I have to edit the set root line in the menu listing in karmic's grub.cfg to (hd0,1) to get "lucid" to boot  even though the linux /vmlinuz  line points at sdd1 .

is there a way to examine the mbr's directly ? I think grub-install is putting grub on the wrong drive .
I think grub put the mbr in the right place. Otherwise it wouldn't show the GRUB error message, right? :)
What kind of controllers do you have? It sounds like that you have multiple controllers which get in a different order on before boot, compared to after boot. When linux boots it will order the controllers in the order their modules gets loaded. This can be entirely different from the BIOS order. (which grub uses)

---

### Post by dino99 on 2009-11-02
hi Lithorus

i'm thinking that way too

---

### Post by ronacc on 2009-11-02
> **lithorus said:**
> I think grub put the mbr in the right place. Otherwise it wouldn't show the GRUB error message, right? :)
What kind of controllers do you have? It sounds like that you have multiple controllers which get in a different order on before boot, compared to after boot. When linux boots it will order the controllers in the order their modules gets loaded. This can be entirely different from the BIOS order. (which grub uses)

my setup may be part of the problem I put each install on its own hard drive and install its grub to that drive and switch bios boot order to set what boots first .

```
test box setup 

primary IDE master  DVDRW
primary IDE slave   none

secondary IDE master  200gb maxtor    karmic original install from alpha3  (ubuntu sees this drive as sdc  bios sees 1st hard drive )
secondary IDE slave   200gb maxtor    karmic fresh install (release) for upgrade to lucid (ubuntu sees this drive as sdd bios 2nd hard drive ) 

sata 1  other distro  
sata 2  other distro 
sata 3  data only   1st drive on controler card   
sata 4  data only   2nd drive on controler card

```

ubiquity saw the drive I installed lucid to as sdd and I told it to install grub2 to sdd . this has always worked in the past with ubuntu installs and with other distros . the only exception was karmic . Karmic is on the drive ubuntu sees as sdc and the bios 1st hard drive (grub drive hd0 ) karmic put its grub on this drive rather than on hd2 which is what sdc should be called . I think what is happening is that ubuntu is naming sata drives first and then ide but grub is seeing ide first then sata , but in no way should ubuntu drive sdd be hd0 .and note that in the grub.cfg it wrote is sets root to hd3 and gets the uuid correct .

edit: some more thoughts , there needs to be some consistency between the way the bios names drives , the way ubuntu and ubiquity names drives and the way grub names drives . and using uuid's in the boot process just makes things worse since neither the bios nor ubiquity or grub show you the uuid .

---

### Post by ranch hand on 2009-11-02
I really would not edit the /boot/grub/grub.cfg file.  It is over written every time "update-grub" is run.

Update-grub is going to be run a lot in this cycle due to kernel upgrades.

Put custom entries in the proper place which is /etc/grub.d.

This is covered in the link in my sig and the first 3 links in it are full of in depth information.

---

### Post by ronacc on 2009-11-02
yes I will do that once I get things straightened out , right now when I'm stabbing around seeing what works and what don't it is easier just to edit grub.cfg .and I keep a copy of a working grub.cfg renamed so that if I really stuff things up I can just boot the livecd ,mount the drive and rename the working one back .Oh and its karmic's grub.cfg that I am editing since I haven't gotten "lucid" to boot from its own grub yet .Look at my first post and you will see that I used your grub2 intro to get this far .

---

### Post by ranch hand on 2009-11-02
Well, Lounge not booting weird.  I updated a Kinky RC to Lounge and had no trouble with it booting.

Right now I am on Stoner Edition 1.0 (9.04 respin) installing updates (clean install) and medibuntu stuff.  I will upgrade to Kinky and then on to Lounge.  I have already removed the /etc/X11/xorg.conf file and have a karmic sources.list and a lucid sourrces.list saved for later use.

---

### Post by tekstr1der on 2009-11-02
> **ranch hand said:**
> Well, Lounge not booting weird.  I updated a Kinky RC to Lounge and had no trouble with it booting.

Right now I am on Stoner Edition 1.0 (9.04 respin) installing updates (clean install) and medibuntu stuff.  I will upgrade to Kinky and then on to Lounge.  I have already removed the /etc/X11/xorg.conf file and have a karmic sources.list and a lucid sourrces.list saved for later use.

@ranch hand - I am assuming your references to build code names Kinky=Karmic and Lounge=Lucid? Is there some distinction between these builds and the equivalent released under Canonical's naming convention? Are they just your own pet names that you prefer to use or do they hold some significance?

---

### Post by ranch hand on 2009-11-02
It is my box and I can call them anything I want.  Yes you are correct in assuming that I am a sick puppy.

Why else would I be here on the testing forum?

I am now upgrading Stoner to Kinky, by the way, and listening to Dire Straits.  I installed grub2 on it before this dist-upgrade to avoid all the problems, or at least get them out of the way.  Works slick.

Need to set up my custom entries but want the the newer grub2 first, before putting them in play.

---

### Post by ronacc on 2009-11-02
@ Ranch hand  I prefer your version for LL , lynx has a bad taste for me , it is the name of the local mass transit system run by a bunch of corrupt ( insert your own explicative's ) . I think that my problem is that grub is putting itself on the mbr of bios drive 1 (hd0 ) no mater where it is told to put itself , my reasoning is when I did a fresh install of karmic back at A3 on the drive that ubiquity called sdc it also boots off of hd0 even though it wrote grub.cfg to boot off of hd2 , now another fresh install from the karmic release cd that I updated at toolchain upload and call lucid is on sdd and boots off hd0 even though it wrote IT"S grub.cfg to boot off of hd3 . told ubiquity each time to put grub on the mbr of the drive I was installing to but it seems to have ended up on hd0 no mater what . I need some way to find out which version of grub is on the mbr of each drive to confirm what I belive is happening and then I will file a bug . This is my test box and has had many things installed on ide 1 and 2 and sata 1 and 2 at this time the layout should be ide 1 karmic grub2 ide 2 lucid grub2 sata 1 and 2 grub legacy sata 3 and 4 no grub . I think I will find that ide2 either has a generic mbr or else grub legacy from an old install .as I stated before sdc AND sdd cannot both be hd0 so there is a skunk in the barn somewhere .

---

### Post by ranch hand on 2009-11-02
I really do not know.

I basically am running 3 drives (SATA).  Two are internal and I turn them off in bios when I boot to my external (testing platform).

It is a dual HDD external enclosure.  I can run RAID  and poot from both drives or not run RAID and just boot from sda.  I don't like RAID so all my / are on sda and /home on sdb (have to put a couple OS' just on sda to keep the usage balanced).

My internals I boot separately too by turning off the one I am not booting to.

In 9.10 testing I did boot from on of my internals to it and the external. Had no trouble with that at all.  Will probably do it againe this time.

---

### Post by ronacc on 2009-11-02
prior to karmic I never had a problem with ubiquity putting grub in the wrong place , I have had other problems with it ,but this is new. I think there is a way to query the mbr's to see what is there but I don't remember ( creeping senility ). I searched the repos and the net for a sector editor like I had for the Amiga that lets you read the raw tracks on a drive but didn't find anything . so anyone that knows how to find out what grub is installed where please post it .

---

### Post by ranch hand on 2009-11-02
That would be nice to know.

I, by the way, would hesitate to climb into the maw of any transport claiming the name "lynx".  Sounds like it could get digestive.

---

### Post by ronacc on 2009-11-02
I finally remembered how to find out which grub is where , supergrubdisk . and lucid did put its grub in the wrong place , having confirmed that I will file a bug against ubiquity . the grub that is on sdd (2nd bios drive) which grub would call hd1 is left over from the jaunty install that I upgraded to karmic at its toolchain start . that had gotten nuked during testing and I installed A3 to sdc and continued testing . I formated sdd twice once with a stand alone gparted and once with the ubiquity from the karmic release cd that I installed to upgrade to lucid . Atleast I have learned that the MBR survives a format .I can tell its that grub because it tries to chainload and the only one I had set to do that was the early karmic when grub2 first arrived .

---

### Post by ranch hand on 2009-11-02
I have found that when updating 9.04 to 9.10 and wanting to use grub2, the thing to do in 9.04 is go to synaptic and remove grub and grub-common.  

Then install grub-pc and grub-common.  This gets rid of all the conflicting stuff and works very nice.  You run update-grub and grub-install /dev/whatever and reboot to check and then upgrade.

I also get rid of all but the generic video drivers and remove the /etc/X11/xorg.conf file.

Goes pretty smooth if you use apt so you can see the screw ups.  This last one I did;
 [http://ubuntuforums.org/showpost.php?p=8228334&postcount=20](http://ubuntuforums.org/showpost.php?p=8228334&postcount=20)
had an error in dpkg.  Ran dpkg --configure -a and it was just a little short deal that would screwup these people that used Update Mangler.  Took about 15 seconds.  No broken packages either.

---

### Post by ronacc on 2009-11-02
I had installed grub2 on that one when it first hit and set up to chainload for testing and then when that install later died I went with grub2 from the start for my reinstall from A3 .

---

