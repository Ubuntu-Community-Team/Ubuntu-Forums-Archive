---
title: "Boot CD problems"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by jp33 on 2007-03-10
I am trying to install on a machine that currently has Win 2003 Server.  I make the boot cd without and issue (I think) but when I try to boot to the cd nothing happens.  I verified the checksum and Infra Recorder without and error to make the cd.  What am I missing, could it be something because I am running Win2003?

---

### Post by Coelocanth on 2007-03-10
Did you go into your BIOS and change it so your optical drive is the first boot device?

---

### Post by jp33 on 2007-03-10
Yes, I also have the same problem with another machine running XP.

---

### Post by Kateikyoushi on 2007-03-10
Did you burn it as image file ? What speed did you use while writing the disc ? When you insert the disc wile running windows does autoplay open a window for you recommending firefox and some other software ?

---

### Post by jp33 on 2007-03-10
Yes I used Infra Recorder and burned as an image.  I used the default setting which should burn at 16x.  When I insert the cd when running under XP I do not see anything.  I assume I should be able to read the content from within X, right?

---

### Post by Kateikyoushi on 2007-03-10
Right, it should run autoloader as well. Burn it at 4X and read this it might be helpful. [LINK]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Kateikyoushi on 2007-03-10
Someone in this thread is using the same cd writing software could you lend him a hand with the installation ? Thanks. [LINK]("http://ubuntuforums.org/showthread.php?t=381109")

---

### Post by Hraefn on 2007-03-10
I have also downloaded and burned (according to instructions in the guide found on the Ubuntu site), and now have a corrupt .pool file.

Will try to re-burn the CD, but not sure if there's a way around this...

Cheers!

---

### Post by Kateikyoushi on 2007-03-10
Someone wrote this week that his cd burner did not play well with a brand of disc he bought results were all coasters, just thought I would mention.

---

### Post by jp33 on 2007-03-10
Interesting comment on the cd-r brand.  I got the big 100 back of TDK's from Costco.  Also tried burning at 4x, still no luck.  Any options I should be aware of using Infra Recorder, Pad data tracks, Fixate the disc after writing, etc??

---

### Post by jp33 on 2007-03-10
I think I am good now.  I deselected most of the options to burn the cd and it worked fine.  One note, I actually was able to burn using one of the discs that previously failed (yes it is a cdr).  I suppose it never actually wrote to the cd, not sure why,

---

### Post by royrules22 on 2007-03-10
May I ask what options do you have slected when you burn because I just coasted 4 CDs. My ISO passes the md5checksum, and when I load the ISO (in Win XP) using Daemon Tools it works exactly as it should. However I tried burning 2 CDs using Nero OEM (which has always worked for me) and it was coasted. I burned another CD using Infra Recorder and that CD too was coasted. Finally I got a different brand CD from my roomate and it too didn't record. The weird thing is that the CDs I had when I orignally put it into my writer, My Computer said that it had 0MB free out of 0MB. After burning it did the same. I tried to fixate that disc using Infra Recorder and then it said 702MB out of 702MB free. I tried burning again onto that same disk to no avail. Now my roomate's disc orignally had 702MB out of 702MB free and after burning it was 0MB out of 0MB free. Fixating it brought it back to 702MB. 

Help?

Edit- Perhaps I should say that I am pretty experienced with ISOs (although most of the time I just use D-Tools I know and have burned them). I'm stumped this time however.

---

### Post by Kateikyoushi on 2007-03-10
It usually just works out for me and I use CD-RW without changing any settings, but here is a real step by step burning guide which should work. [LINK]("http://www.psychocats.net/ubuntu/iso")

---

### Post by royrules22 on 2007-03-10
> **Kateikyoushi said:**
> It usually just works out for me and I use CD-RW without changing any settings, but here is a real step by step burning guide which should work. [LINK]("http://www.psychocats.net/ubuntu/iso")

Nope that doesn't work either. :mad:

---

### Post by Kateikyoushi on 2007-03-10
Maybe your burner ? Could you ask someone else to burn it for you ?

---

### Post by royrules22 on 2007-03-11
It should not be my burner as I just burned another ISO (not Ubuntu) about 10 minutes ago, because I had the same suspicsion as you. Apparently burner is perfectly fine. WTF..

---

### Post by Kateikyoushi on 2007-03-11
Are you sure your download is not corrupted ? He explains how to check it with md5sums. [LINK]("http://www.psychocats.net/ubuntu/iso")

---

### Post by royrules22 on 2007-03-11
From my original post:

> **royrules22 said:**
> My ISO passes the md5checksum, and when I load the ISO (in Win XP) using Daemon Tools it works exactly as it should. 

Sorry if I sound a little rude or pissed off, it's just that I never thought that the hardest part of setting up Linux would be burning the damn CD :p

---

### Post by Kateikyoushi on 2007-03-11
Sorry I just can't figure out how could this happen that a good file and good burner with good discs do not result in readable burned disc.

One last thing, did you burn the disc faster than 4X because using higher speed can mess up the ubuntu boot discs.

---

### Post by royrules22 on 2007-03-11
That is a good point. I did it at 20x. Lemme try again at 4x. Oh and I wish the OP would respond and say what settings he or she used.

---

### Post by royrules22 on 2007-03-11
Yes it works! Woot! Burning at 4x speed did the charm. So after 5 coasted CDs it's finally done!
Thanks!

---

### Post by Kateikyoushi on 2007-03-11
I should have think about it sooner, lesson learned.

---

### Post by royrules22 on 2007-03-11
Argh I'm seriously going to cry here. This is BS. I burn it at 4x and it finishes correctly. I go to My Computer and I see that the CD says Ubuntu with it's logo, so I'm happy it works. Apparently though the computer hung when it tried to autostart. So in any case I said hey it's burned so let's boot from CD. First time, no luck. Ok go to BIOS and change order. Now it boots from CD first. Reboot. Nothing. Go to my computer. Reads as a blank disk WTF!!! Burn new CD. Burned correctly. Reboot. Nothing. My computer says blank disk. 

W.T.F..

---

### Post by jp33 on 2007-03-11
What software are you using to make the cd?  Like I stated earlier, I am using Infra Records, as recommended and had no luck until I pretty much deselected all of the options.

---

### Post by kboykowboy on 2007-03-11
I have same problem - i'm burning it on my mac ibook g4... the minimum speed on it is 8x?! could that be the problem!? (by the way it is xubuntu)

---

### Post by royrules22 on 2007-03-11
> **jp33 said:**
> What software are you using to make the cd?  Like I stated earlier, I am using Infra Records, as recommended and had no luck until I pretty much deselected all of the options.

I use Infra Recorder and the only options I have selected is:

4x Speed
SAO (Session at Once)
Pad Data Tracks
Fixate Disk after Writing

I just burned another copy and although it says it finished burning looks like the disc is still empty..

---

### Post by royrules22 on 2007-03-11
Is bumping allowed here? (*wink*)

---

### Post by kboykowboy on 2007-03-12
what's bumping?! anyway - i found that a program for mac called Disco can burn all the way down to 1x - i have burned my disk but cant try it out untill later today ;-) talk to you all later

---

### Post by kboykowboy on 2007-03-12
Hey U'all - I have got it running now! 

I used my ibook g4 with the program disco (latest version) i burned the disk at 1x speed... that did the trick! 

good luck to you all in this string!

K

---

### Post by royrules22 on 2007-03-12
Still can't get it :(

---

### Post by darsu on 2007-03-12
I could use some advice burning the 6.10 ISO.

I have 5.10 right now, the ISO is sitting over there in ~/tmp. I've tried burning it with mkisofs+cdrecord:

mkisofs -R -o /home/(me)/tmp/kubuntu-6.10-desktop-i386.iso .
cdrecord -v -data /home/(me)/tmp/kubuntu-6.10-desktop-i386.iso

I've also tried twice with K3B, first with custom settings and then with whatever settings it gives me as defaults. 

All three times I've ended up with a CDRW that contains the .iso file in a filesystem. I can't figure out what I'm doing wrong.


Edit: I took another two hours to re-d/l the ISO and it worked fine. Shrug.

---

### Post by royrules22 on 2007-03-13
Well I installed it... by using a friend's live CD

---

