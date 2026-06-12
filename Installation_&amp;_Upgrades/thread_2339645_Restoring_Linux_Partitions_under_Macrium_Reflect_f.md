---
title: "Restoring Linux Partitions under Macrium Reflect free edition."
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by jakemaverick911 on 2016-10-11
I really can't believe this is happening to me- I have been so careful!  But basically I have been using Macrium Reflect for years and always  found it has worked very well. In the past I have only used it to  restore Windows partitions.

Couple of days ago my SSD failed. So I've been trying to restore my  backup...first time I have ever had to restore a linux partition. But I  was not expecting it to be a problem as it has been backing up, so I  thought, Linux partitions happily for years...

Basically what I think is happening is that it is ignoring the linux  file structure and restoring the raw data onto Windows type  positions....for example it ignores the 4 gig Linux Swap 'partition' and  just restored 243mb and leaving rest of partition as unformatted space  and the linux swap area becomes formatted to Ext 2....for the main linux  partition it does similar but loses it's Ext4 or 3 formatting....

So I think the data is basically there....I just need a bit of help in tweaking it I think to make it bootable?

Unofrtunately I'm very poor and it's the free edition I'm using....so no  support from Macrium, but as the data is physically backed up there has  got to be a way to sort this?

worse possible nightmare imaginable and it's so frustrating as I took  every precaution.......and that SSD is literally only couple of months  old from new......who knew they can just fail like that with absolutely  no warning whatsoever? :-(    

I don't think it really matters but I was using the Xubuntu flavour and had just upgraded to the latest version.

---

### Post by Bucky Ball on 2016-10-11
Just wondering why would you would be backing up a /swap partition? Is this a full disk clone you're trying to do? 

As on another thread, Macrium has no Linux version. Not surprising it doesn't deal with EXT* partitions. It's Windows software for Windows backups.

If you are using Macrium in Win, which is kinda inevitable, Windows has no idea what EXT* partitions are so not surprisingly, neither does Macrium by the looks.

You could try testdisk and/or photorec, both of which are available on the [SystemRescueCD]("http://www.system-rescue-cd.org/SystemRescueCd_Homepage"), along with a bunch of other handy apps. Do a search, download the ISO, create bootable media from it, boot from that and see what you find.

Important thing is, if you think the data is still there, DON'T use the disk for anything apart from retrieving data, or trying to. The more you use it, the less chance of your data surviving. Using it will write over any blocks marked 'writeable' which may appear to the user as empty space but actually still contains  data.

* Belated rule of thumb for partition or disk backups: always make sure they worked and you can restore to another disk before proceeding!

---

### Post by jakemaverick911 on 2016-10-11
OK thanks....er what other thread though? couldn't see anything which was why i posted...

Relatively still a newbie in lunux though...and I couldn't find anything to backup from within linux and doing a search will tell you that you can use Macrium to backup linux via windows and for last couple of years it seemed to be doing exactly that....

yes it was full disk backup which was why swap went over as well....two physical disks actually....which is why i can still boot to XP! i'll earch for what u mention....but can they physically read macrium backups? sounds unlikely

---

### Post by howefield on 2016-10-11
> **jakemaverick911 said:**
> Relatively still a newbie in lunux though...and I couldn't find anything to backup from within linux

Have a look at the excellent Clonezilla, it probably doesn't look as user friendly as Macrium but it works very well.

> and doing a search will tell you that you can use Macrium to backup linux via windows and for last couple of years it seemed to be doing exactly that....

Of course, you are quite correct, from the user manual....

> Supported File Systems
Imaging clusters in use and changed clusters (intelligent copy) is supported by FAT16, FAT32, NTFS and Ext 2,3,4 file systems. All other file systems and unformatted partitions will be imaged on a sector by sector basis, i.e, every sector in the partition will be copied.

So even if it doesn't "support" the file system it will image sector by sector.

Not that this helps you with your problem, just suggesting an alternative for the future :)

---

### Post by jakemaverick911 on 2016-10-11
thanks man- i have come across clonezilla since, not used it yet though....it's just that i didn't think i needed it as macrium was supposedly doing the job.....:-(

Just tried the System Restore CD and no joy there I'm afraid...I can get into GParted alright, but only option there is to reformat the partition and that would destroy the data. Couldn't find an option to just change the type....

Another thought though...the system is encypted. Is there anyway to external log into it and unencrypt to get the data off without physically booting from that partition?

---

### Post by Bucky Ball on 2016-10-11
Ah, encrypted! That may be your only problem. Have no experience whatsoever with encrypted partitions, sorry, so good luck. :)

---

### Post by jakemaverick911 on 2016-10-11
I don't think it's the fact that it is encrypted which is causing the problem....it's just the partition formats I think. Needless to say I am extremely p'eed off with Macrium :-( Talking many years of work and personal data here....I mean what are the odds? SSD judt dying, then corrupted backup then it turns out Macrium is full of s*** on this as well.....
Even though they don't support the free edition I just got an email from them confirming yes you can back it up but can't guarantee successful restores because it's not supported now.....:-(  People really need to know about this!

Has anybody bought the full version of Macrium? I suspect that it may be a case of that will work as it has a lot more options within it, judging by the screen shots.....but I'm pretty destitute and don't want to buy it on the off chance...and can't get any sense out of support. If that would definately solve it then i would try and find the money...but even then would be loath to do so.....

as it's done it 'sector by sector' i just can't see why it would not be possible to lay it back down exactly like it copied it in the first place...

---

### Post by howefield on 2016-10-12
I have no experience whatsoever regarding Macrium, but from a rereading of this thread, all you've told us is what you think is happening, not what actually is happening.

So you restored the Macrium image, what then happens ?

---

### Post by howefield on 2016-10-12
I have no experience whatsoever regarding Macrium, but from a rereading of this thread, all you've told us is what you think is happening, not what actually is happening.

So you restored the Macrium image, what then happens ?

---

### Post by jakemaverick911 on 2016-10-12
Well, I can see the partitions in Acronis....the data does restore but rather than it being on an Ext 3 or Ext 4 Partition there is none.....(Acronis can't see Ext 4, so calls them Ext 3 when it does see them).

When I try someof the boot options from System Restore CD, such as boot linux from the disc....the texts flies by pretty quick....but it looks like it can see the data there but falls over before it boots into it. Think it said it was missing a file but there weren't any errors on the restore so I suspect it is still because of the Partition issue.

Now usually you can change the partition type in Acronis without formatting, but when I try and change it back in there I can't- Partition type is none and there's no option to change it. Does any of that help at all?

if i can find a way to change the partition type to ext 3 or ext 4 without having to format it.....might solve it?

actually, just tried AOMEI partition assistant....now it does give me options in there to change partition type...but alas, no easy option to change to Ext 3 or 4....but there are lots and lots of options- I'm wondering if one of them is long winded name for same thing?
it also sees it as 'linux native' although partition type is still 'none'....so probably no better off :-(

---

### Post by Bucky Ball on 2016-10-12
What does Gparted see it as? Boot to a Ubuntu install disk live session 'Try Ubuntu' and have a look.

---

### Post by jakemaverick911 on 2016-10-12
have just found [http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

but it still won't read the disc from within windows, presumably because it's encrypted :-(

> **Bucky Ball said:**
> What does Gparted see it as? Boot to a Ubuntu install disk live session 'Try Ubuntu' and have a look.

i will give it a go, but i dnt think it will work as the partition is encrypted....i know the password though, must be a way to 'access' it.....I wonder if I did a complete install to a new disc, set it up with same password and then tried to ook at it....would that work? ;-)

if i can just get my data off and all my firefox data and tab settings- it would be something

ooh! nice surprise.....botting from the xubuntu disk, it allowed me to put in the password this time and i can access that parition! Finally! so hooray, thanks guys....!

but another slight problem....although i can see all the files on the drives now, some have an X over them 'permission denied' problem...so there's a good 3gig of data i still can't access- and it is all the files i really need. i'm still arguably a total noob....but i'm guessing it's a case of doing something in terminal via sudo or something, then i will be able to copy all my data off?

but nearly there i think, yay! just that lil bit i still need some help with....+ i also had the thought if i re-install OS to a new disc.....can i just copy over and over write the Home directory to get everything back, or will that not work?

CheerZ again!

oh, i say surprise as i have tried that before and it did not accept the password for some reason- but this time it did!

just trying to restore the corrupted backup via robocopy....apparently that should work but keeps falling over after a few seconds....looking at the .txt file it's soemthing to do with G: drive, but there is no G: drive! make sense to anybody? ;-)

working on this since Sunday now and starting to go goggle eyes....:-( what i'm now thinking is to find a way to view the encrypted file partition for Xubuntu in windows...then hopefully i shall be able to recover all my important data from the most recent backup /home directory and just copy it across....

apparently that is possible but all the links that tell you how to do it are now dead.....anybody know?

what i'm thinking is that on that corrupted backup the home directory might be perfectly ok.....so this would now be best way i think if it is at all possible?

um, i've never used virtual boxes....but if i can figure that out, install xubuntu within that then mount the corrupted image file, could i then share the directory with windows that way? sounds like a lot of work if i can pull it off......but i would rather know that wd definately do it before i did it? ;-)

tiny update... I read that the command do resolve the file permissions problem was gksudo nautilus.... so booted from live CD, tried that did not work as it was not installed so i intalled it (don't know where it installed it as I was booting from the CD....) but it still did not work....

ok, finally got xubuntu working in a virtual box (lot harder than it  sounds, believe me) but now i need to install guest additions.....and it  just not happening, has anybody done this before?

---

### Post by howefield on 2016-10-14
> **jakemaverick911 said:**
> ok, finally got xubuntu working in a virtual box (lot harder than it  sounds, believe me) but now i need to install guest additions.....and it  just not happening, has anybody done this before?

Where are you stuck ?

[https://www.virtualbox.org/manual/ch04.html#idm1948](https://www.virtualbox.org/manual/ch04.html#idm1948)

---

### Post by jakemaverick911 on 2016-10-14
managed to sort that one now....cdn't get it to install from the virtual cd drive, but managed to get internet working so installed it via ap-get

but, here's the biggy now....had this working under XP no problem [http://www.ext2fsd.com/?cat=3](http://www.ext2fsd.com/?cat=3)   but for some reason i just can not get it to work under windows 7

that really is last bit i think, if i can make that work i should, hopefully, be able to salvage my data from that corrupted backup

---

### Post by Bucky Ball on 2016-10-14
Have you successfully restored your Linux Partition under Macrium Reflect free edition? If so, rather than start asking new support questions here, you'll greatly increase your chances of support by marking this as solved and starting a new thread for any new issues. Good luck. 

(PS: What you're asking about is a Windows support issue now.)

---

### Post by jakemaverick911 on 2016-10-14
yeah i get that ;-) it's not solved though until i can sole this niggly little problem sorted now....I'll probably close this in a bit, if that's ok....regardless of whether i can fix it or not ;-)

ok still a nightmare....but slightly different problem now, it's all  related to the above so dnt think it's worth starting a new thread...

but where i'm at now:
done a new install of xubuntu
trying to copy across data from the old backup that isn't corrupted but has not restored right
so trying to copy home directory across....

here's  the weird thing....i can't access that encrypted partition at all from  the new install, refuses to mount. but f i boot from the CD i  can....but....file permissions problem? the only way i can access that  directory (home) is via the CD....and their's loads of files and folders  that it won't give me permission to access.

now reading on toher  forums the way to do it is to type gksudo 'nautilus' in a terminal  window. 'cept that doesn't work....is there another way to access that  data?

and 2 i think all my settings as well as data is stored in  the home directory as far as as my understanding goes...i.e. monitor  settins and programmes, session restore for firefox etc....and they have  all copied across to the new install....but Xubuntu still not taking  any notice of that....is there anyway to get it all back how it was  originally? i would have thought simply copying home directory across  would do it...presuming all the config data is in there?

---

### Post by Bucky Ball on 2016-10-15
Well, you could try with the complete command if you're not already:

```
gksudo nautilus
```

---

### Post by jakemaverick911 on 2016-10-16
yes i have tried that, even after it installed it did not work....said nautilus was invalid command also, so i guess something to do with xubuntu flavour?

---

### Post by Bucky Ball on 2016-10-16
Xubuntu?

```
gksudo thunar
```

You don't have Nautilus installed.

---

### Post by jakemaverick911 on 2016-10-16
thank you! i knew it wd be something like that ;-) but 'fraid too late now...i'm actually in the new xubuntu install now and managed to get my entire home directory across now by sudo cp -rp /home/user /home/user.backup   it did skip a few superlong file names on the restore, which struck me as odd, but they're not important

that seems to have worked, but none of my settings or programmes have actually gone across, i have rebooted....just realised something....might be because i made a boo boo on the install by calling the machine different names, how do i change that? changing it in hostsname and hosts doesn't work as it will not allow me to save the changes.

and i'm starting to suspect that there might be other config data stored elsewhere other than the home directory? i keep thinking i'm nearly there then hit a brick wall :-(

actually, post 24 here seems to have done it

[http://askubuntu.com/questions/9540/how-do-i-change-the-computer-name](http://askubuntu.com/questions/9540/how-do-i-change-the-computer-name)

and i was quite hopeful as it was whirring away quite a bit after too reboot....unfortunately nothing has changed, new config data still not loaded at all :-( so all i can think is it that it has got to be something else that is not in the home directory?

just been reading on other pages...but it gets very complicated, especially as i don't have a bootable system that I'm trying to recover these settings from....but on what i just read seems lot more config data in /.etc    if i can manage to copy that over in it's entirety/ overwrite.....would that fix it?

actually just did that and it did not work either :-( i need to get some sleep i think

---

### Post by jakemaverick911 on 2016-10-17
u know what it was....i had forgotton about ctrl H to make hidden files visible...seems some of the hidden files had gone across but not all of them....so clean install and copied over home directory with the hidden files and it's not quite done it but pretty much there i think.....so thanks for all your help folks and please close this thread

cheerZ!

---

### Post by Bucky Ball on 2016-10-17
Great. We don't close threads, you mark them as solved by using Thread Tools at the top right. Any confusion, please see the last line/link in my signature at the bottom of this post. Thanks.

Marking 'solved' does not close the thread to further discussion.

---

