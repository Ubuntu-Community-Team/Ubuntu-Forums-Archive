---
title: "All going suspiciously well."
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2009-12-11
Apart from loosing ethernet - which could be the router down - as i cannot access it from 9.10 either. My 3G usb modem is working fine.

All seems well. I got the restricted formats from here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But, ```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reports file not found - I'm guessing the command to get the dvd codecs is different in 10.04.

Has anyone had any issues with putting LAMP onto the desktop edition of 10.04 alpha ? As that's next on my list of things to do.

Regards,

Phill.

---

### Post by mc4man on 2009-12-11
> Reports file not found - I'm guessing the command to get the dvd codecs is different in 10.04.

Same command as before to install libdvdcss2, actually lucid is using the same libdvdread4 as karmic

As far as using the ubuntu-restricted-extras meta ppackage, (if you did), you may or may not be getting what you wanted. It will install the 'stripped' versions of ffmpeg libs, though for many that won't particularly matter

---

### Post by ranch hand on 2009-12-11
I even broke my A1 and later booted t o recovery, ran "dpkg fix broken packages" and the bugger is up and running fine.

Just HAD to (I have 4 installs) run an "apt-get dist-upgrade" to see what would happen.

---

### Post by phillw on 2009-12-11
> **ranch hand said:**
> I even broke my A1 and later booted t o recovery, ran "dpkg fix broken packages" and the bugger is up and running fine.

Just HAD to (I have 4 installs) run an "apt-get dist-upgrade" to see what would happen.

lol.

my system barely flinched when i did an ext3 --> ext4 translation, just a quick e2fsck.. Sturdy little bugga's, aren't they :-)

Heading the advice earlier about keeping lucid away from my Karmic area - I rsync'd my home over -- Another wonderfully painless excercise. Heck, these devs are good :D

I'll go nag lovinglinux later - I've been reading the threads on Flash for 10.04, but sure how to proceed.

Oh, and it must have been a network problem -- the router is back up and running.

Good to hear all is well for you !!

Regards,

Phill.

---

### Post by kansasnoob on 2009-12-11
I'm also amazed at how well Alpha 1 runs.

The only odd thing I notice is when I reboot or shutdown I get a screen full of rectangular blocks of every color in the rainbow for maybe 30 seconds.

Something I find amazing is that both my cpu and gpu temps run a bit lower in Lucid than either Karmic or Jaunty. Lower temp means it's using less juice I'd think????????????

And yes I'm sort of a tree hugger. Not extremely so but I do believe it's responsible to use as little of the earth's resources as possible and still live comfortably.

I am however running the Xorg crack updates thru their ppa.

---

### Post by Merk42 on 2009-12-11
Noticed a small bug, but I'm running in a VM so I dunno if that's the cause.

If I deliberately get my login password incorrect it resets back as it should. However if I then hit Enter to retype my password GDM seems to glitch and completely redraw itself.

---

### Post by yoasif on 2009-12-12
> **Merk42 said:**
> Noticed a small bug, but I'm running in a VM so I dunno if that's the cause.

If I deliberately get my login password incorrect it resets back as it should. However if I then hit Enter to retype my password GDM seems to glitch and completely redraw itself.You may be seeing this bug:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/491673](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/491673)

---

### Post by phillw on 2009-12-13
Lamp on, MySQL dbase transferred over... next up .... ossec ... It will be e-mails-R-Us with all the various pkg releases !!!!

So far, so good :-)

---

### Post by phillw on 2009-12-13
> OSSEC HIDS Notification.
2009 Dec 13 21:35:50

Received From: piglet->ossec-monitord
Rule: 502 fired (level 3) -> "Ossec server started."
Portion of the log(s):

ossec: Ossec started.



 --END OF NOTIFICATION


I'd say that's a working installation :-)

Phill.

---

### Post by phillw on 2009-12-13
Has anyone had a 'play' with anything like this, yet ?

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I got part way through v8 on my 9.04 system, but haven't had a 'play' with it since.
(I borked my system by incorrectly setting up SSH - and got hacked, not something I'd be doing again in a hurry !!)

I'll be trying out v9, the RC for 9.10, -  hopefully, it is 10.04 aware ;-)

It should allow 10.04a to 'stretch its legs' as nothing I've asked of it so far has troubled it in the slightest.

Regards,

Phill.

---

### Post by darco on 2009-12-14
> **phillw said:**
> 

I'll go nag lovinglinux later - I've been reading the threads on Flash for 10.04, but sure how to proceed.



Flash 10.0.42.34 x64 running fine in Lucid. Used the script (sticky) in the recently decommissioned x64 bit forum.


darco

---

### Post by phillw on 2009-12-14
Hi - I wandered accross this thread --> [http://ubuntuforums.org/showthread.php?t=1352947](http://ubuntuforums.org/showthread.php?t=1352947)

got me up & running - although you may need to get the latest release number from Adobe. - I just downloaded the most recent one and popped the .so file into my ~/.mozilla/plugins I *think* it is slightly different for you 64 bit'ers. But mine is happy, no choppy video etc.

Phill.

---

### Post by phillw on 2009-12-31
Look at the time stamp.... look at all the posts in between....

Yet, I stand by the thread title

We all log on here and moan about what's broken (in some cases without bothering to read the threads and find a solution, or if it is a known bug --- Those ones really .... me off)

Can I say, in my little IMHO, that I prefer to run 10.04 than I do 9.10 - It is more responsive, snappier, more graceful if an app curls its toes up and does no longer want to respond. I love what they're doing with the notifications, I follow the death of 100 paper cuts & also the bulletins of what is going on.

On the bulletins ... I sorta understand 5% of it, but if it is package I am aware of, I'm all ears and reading avidly... there are some really weird package names, getting to read a brief description of them is educating. 

Heck, boyz & girlz - This is gonna be one heck of a release. 
Privately, I do whisper to those having issues in 9.10 that the devs are **really** concentrating on 10.04 (Honest, I've not told them that 9.10 ***is*** the pre-alpha -1 of 10.04 -- lol)

That is not against policy, we were told in 9.10, that we had max, 2 weeks, to flag up major stuff before they all got bored and went to play with 10.04 - It was a busy 2 weeks, I'm still not sure if I forgive them for dropping Grub2 onto us.

The person who wrote most of the Grub2 stuff, who we all know, told me that it was sort of an after thought ..... OOOhhh, documentaion, instructions ..... Yeah, well, you can do all of them. He's one heck of a guy.

As for RAID, well, from being totally "well, whenever" the penny seems to have dropped that they are actually going to have to make it work. 

Again, people on 9.10 who I am saying to - be patient. (Worked fine under grub legacy -- guess what the work round is, you ... drs305's - put grub legacy back on your system)

But - you haven't broken mine, yet !!  Things to be grateful of ... A bog standard laptop, wrapped in aircraft grade aluminium chassis, all Intel M Processor 440, 1GB RAM and 80 GB Disk.... Heck, but it's running a LAMP server (local) on 9.10, 10.04 and even has it's Vista area still installed.

I was chatting to my Brother about games on computers -- I think he does, actually, have a point. Have a computer, to do computer stuff with. Have a Games machine to do, well, Games stuff with. You can pay more for a video card than a top of the range games console ?   Weired 

Yes, you'll all be glad when I can post back to my own blog.

My kindest regards to you all.

Phill.

---

### Post by QwUo173Hy on 2010-01-03
Good gaming thread over here: [http://ubuntuforums.org/showthread.php?t=1241660](http://ubuntuforums.org/showthread.php?t=1241660)

Max is find great linux titles and interviewing developers of upcoming games - I'll be surprised his site doesn't make it's way to your bookmarks.

---

### Post by SnowRider on 2010-01-03
Seems I'm a little late jumping on the bandwagon.Used a partition that I've been using for Distro hopping.Popped in a copy of Karmic,updated & upgraded it.Then did update-manager -d to get Lucid.Enabled nvidia-vdpau ppa & Firefox&Chromium daily builds.I haven't had any problem's.Everything is running perfectly,even flash.Youtube videos run flawless.I AM IMPRESSED.\\:D/

---

### Post by ronacc on 2010-01-03
all going very smooth here too . I nuked my 9.10>10.04 update a couple of weeks into the run but that was my fault , installed A1 and hve only filed 1 bug and added 1 me-too . A low for me in a long time:P

---

### Post by VMC on 2010-01-03
I'm looking for double the trouble. I have both Ubuntu and Kubuntu Lucid testing. Ubuntu gives me little trouble, but Kubuntu has several Segmentation faults, all from shutdown - log-off, restart or shutdown. I'm sure this is a KDE issue and have filed a bug report at kde.org.

---

### Post by ubername on 2010-01-03
Also annoyingly painless here.

My two gripes are network browsing
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/490201)

and wake from suspend causes random coloured ascii blocks , requiring restart. Using nVidia 195.22. I haven't pursued this one as there is (has been) a lot of probs with nVidia generally so I thought I would wait and see. Anyway, it's a dev nv driver in a dev o/s so what can I expect? That it works at all is brilliant.

---

### Post by garryknight on 2010-01-03
Even more boringly painless here. I installed Kubuntu 9.04 in June last year and everything went really well from day one. Then in October I let it upgrade to 9.10 and it's been at least as good ever since. The only problem I've had is that sometimes KDE leaves a button on the task bar after a program has closed, but this has only happened a couple of times. Oh, and a network routing problem that I've documented _[elsewhere]("http://ubuntuforums.org/showthread.php?t=1362198")_.

I've also installed Kubuntu 9.04, and upgraded to 9.10 on an MSI Wind-clone netbook, and installed 9.10 from scratch on an EeePC 4G. And KDE runs well on both; in fact, it's smoother on the diminutive EeePC than on the Wind clone.

---

### Post by k3lt01 on 2010-01-03
My laptop is going pretty well. Actually Lucid is doing better than Karmic on it. Karmic is slowing down occasionally, I think it may be to resource hungry for my laptops specs, but Lucid is performing as well as I could hope for.

My only beef with both is because of ureadahead. Everytime it has to reset itself it takes ages, 20 minutes to half an hours is nothing out of the ordinary.

I am currently debating whether to ditch Karmic on this machine or not. It is my main machine but I keep a copy of all my important things on my Jaunty desktop.

---

### Post by phillw on 2010-01-04
Hmmm... Dare I ....

I've got to an install on a laptop Acer for my Mum ..... 10.04 or 9.10, this is the question ?!!

Guess I'd better play safe and put 9.10 on - although, I might just set it up tri-booting like this one does. (It will also have a legacy XP area as the accounts s/ware only runs in Mac or Win & I'd rather not play with WINE on the backup accounts system - just in case). One for a rainy day to play with - I've got to learn a bit about WINE 1st & will probably w8 until 10.04 is out fully & just do it that way.

Glad the icons in Weather Report 2.28.0  work now - that's a really sweet little programme, so thanks to who-ever pointed me towards it.

:popcorn:

As ever, the updates to 10.04 are coming through thick & fast .. too many to mention, get on the mailing list & keep up with things - If an update borks something, you'll have an inkling as to which update did it & can let the devs know pdq.

Happy testing 

Phill.

---

### Post by slakkie on 2010-01-04
Going well? I've had some many lucid problems it isn't funny. Debian unstable :guitar:

---

### Post by phillw on 2010-01-04
> **slakkie said:**
> Going well? I've had some many lucid problems it isn't funny. Debian unstable :guitar:

I'm sorry to hear that, but it's good in some ways as you can report them & they can fix them (You **are** reporting them ?!!) - My machine is totally useless for testing on - It just sits there like a good little piglet & carries on working :lolflag:

/edt ... you know when you type something ... then think it wasn't such a smart thing to do (like rm -r) ... I hope I don't regret just posting the above !!!!

Regards,

Phill

---

### Post by dino99 on 2010-01-04
not so well:

 when i boot, gdm don't start and i can't call a console, so that fail

---

### Post by slakkie on 2010-01-04
> **phillw said:**
> I'm sorry to hear that, but it's good in some ways as you can report them & they can fix them (You **are** reporting them ?!!) - My machine is totally useless for testing on - It just sits there like a good little piglet & carries on working :lolflag:

Regards,

Phill

I would report them, but when I'm unable to boot or login I don't feel the need to report a bug and just happily boot up Debian unstable. Which proves to be more stable then Lucid.

---

### Post by phillw on 2010-01-04
> **slakkie said:**
> I would report them, but when I'm unable to boot or login I don't feel the need to report a bug and just happily boot up Debian unstable. Which proves to be more stable then Lucid.

  We're not due to 'freeze' from debian until Alpha3 - And, with the rate the changes are going through at one day's image can be quite different to the previous day's. Could you not get alpha1 to boot ? (excluding on going problems with nvidia drivers). The staged releases, like alpha1, were *supposed* to be, at least, bootable :-|

Ah, well - there'll be a new image tomorrow -- I still only have the Alpha1 RC as my re-install point. (But it was only 48 hours before A1 was released).

Phill.

---

### Post by slakkie on 2010-01-04
A1 booted, but KDE got borked (crash and burn), KDE got fixed, but then apt broke aptitude (fixed a day later) and I believe the last update left me without sound.

---

### Post by phillw on 2010-01-04
YAY .... RAID is coming to grub2 (read the release notes !) SATA-RAID and some other tidying up with RAID arrays. Also better support of Grub2 on removable drives - It's quite involved - so do go have a peek !!!  -> [http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg02406.html](http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg02406.html)   That's also where you can find the others.

Dunno if they've just had a shake-down, but the 15 - 20 , or so, things done each day has jumped upto about 100+ ....   Ooooh, my poor brain cell - They've been stuff with the ubuntu-install suite, also - all i need now is someone to teach me how to translate it into english .....  Where's **23meg** ? He's good at this sort of thing. When an update is accepted via the emails - how long does it take to get into the next daily image ?

 :lolflag:

Phill.

---

### Post by Jordanwb on 2010-01-04
Aside from gdm deciding to terminate upon bootup (may be plymouth related) and a program not working right in Wine; everything's going fine. :guitar:

---

### Post by phillw on 2010-01-04
> **slakkie said:**
>  I believe the last update left me without sound.

Are you sure it didn't just mute one of the sound devices .... The pesky critter did that to me a while back .... Blooming Carnivores ;-)
Also, watch for it installing the hardware modem driver and enabling it - that borks sound, also, on my machine.

Regards,

Phill.

---

### Post by slakkie on 2010-01-05
> **phillw said:**
> Are you sure it didn't just mute one of the sound devices .... The pesky critter did that to me a while back .... Blooming Carnivores ;-)
Also, watch for it installing the hardware modem driver and enabling it - that borks sound, also, on my machine.


No, my Debian KDE also registers something regarding pulseaudio after a Ubuntu boot. Just booted Ubuntu btw, will have a go at it today. The KDE network manager seems to read the interfaces file.. Since it displays all my mappings. Nice, not needed but nice.

Seems my sound is fixed now too.

---

### Post by garryknight on 2010-01-05
I said my Kubuntu 9.10 was running well. I have to take that back. I tried the webcam in my Wind-clone netbook for the first time since upgrading to 9.10 and it's no longer working. So I did some Googling and it seems that others have had the same problem.

And now my EeePC 701 4G (9.10 installed from scratch some weeks ago) has also started misbehaving: it boots then a dialog comes up saying that a sound device has been removed (not by me, it hasn't!), and then the WiFi card doesn't work. If I keep rebooting, both problems eventually sort themselves out, so it seems that they might be connected. Mind you, the webcam on the EeePC *does* work.

---

### Post by ranch hand on 2010-01-05
> **garryknight said:**
> I said my Kubuntu 9.10 was running well. I have to take that back. I tried the webcam in my Wind-clone netbook for the first time since upgrading to 9.10 and it's no longer working. So I did some Googling and it seems that others have had the same problem.

And now my EeePC 701 4G (9.10 installed from scratch some weeks ago) has also started misbehaving: it boots then a dialog comes up saying that a sound device has been removed (not by me, it hasn't!), and then the WiFi card doesn't work. If I keep rebooting, both problems eventually sort themselves out, so it seems that they might be connected. Mind you, the webcam on the EeePC *does* work.
And this pertains to 10.04 how?  I think I must have missed something here.

---

### Post by garryknight on 2010-01-05
Sorry. Didn't notice the forum title. :redface:

---

### Post by ranch hand on 2010-01-05
Ah, that would be it then.  I am so glad of that.  I am a grumpy geezer and I thought maybe I was just losing it all together.

---

### Post by phillw on 2010-01-09
> **ranch hand said:**
> Ah, that would be it then.  I am so glad of that.  I am a grumpy geezer and I thought maybe I was just losing it all together.


Surely not ?!!!  :lolflag:

You're just in the same club as me .. 99% of the time  :confused:  and 1% :rolleyes:

Must say, still hasn't killed my system yet (although I nearly did)

There's some more stuff out for the nvidia gang, to keep them out of mischief.

Grub has had a couple of add-ons, and about 1,000 other things that I can't keep track of .... Oh, yeah, they've sorted out a couple of bugs in the bug-reporting part ....

Phill.

---

### Post by Ibidem on 2010-01-09
Here it's mostly working.  Wireless (AR5007/ath5k) is fine, ethernet (Realtek 8102e/r8169) is fine (that's how I installed), Intel 945/i915 graphics haven't grumbled, the webcam works OOB, but I met two issues:
1. My favorite file manager, PCManFM, requires HAL so it can automount flash drives--NOT WORKING
usbmount does the trick
2. Realtek "ALC268" audio does not work OOB.  I'll "research" before any bug reports.
Anyone else have hints?
All in all, that's not bad--far better than some final releases.
Then the boot time is phenomenal.
Ibidem

---

### Post by Eestlane on 2010-01-09
At last! I can play Extreme Tux Racer (fps now ~30, in karmic ~5). It might be I had xorg-edgers in software sources before (which made Ubuntu crash though), though removed it before last upgrade.

---

### Post by phillw on 2010-02-03
Well, having had 10.04 well behaved - I have decided to let it have a 'play' with some real world stuff. So, with much backing up...

10.04 now has a 'live' version of one of the sites I've been building to have a 'play' with along with the LAMP server.

I've had LAMP on for a while & it has behaved. Same with Bluefish and Filezilla.  But, we can't keep the kid wrapped in cotton-wool & bubble wrap for-ever - time for 10.04 to have a stretch, see the outside world and get used properly. 

So, if [My Dads Works Site](http://mgjuddltd.co.uk) suddenly vanishes - It won't be 10.04's fault as the site is hosted away from my computer, my computer will just be doing all the coding and testing of code prior to being uploaded to the main server.

If anyone wants some data for testing on a Server running as a server, you're welcome to ask - the whole site (including the images) comes in at a shade under 10MB (9 MB of technical Drawings / Photos, 500K of MySQL dbase with about 1,500 records on it, and about 100k in php code)  Feel free to ask !!

Regards,

Phill.

---

### Post by OrangeCrate on 2010-02-03
I've come late to the party this time, and I just downloaded Alpha 2, and installed it this afternoon.  I'm just short of amazed with the stability I've seen so far. Everything I use regularly, is working fine, with the exception of a couple of small issues that were present for me in Karmic, that remain here. I was not happy with Karmic, but so far, I'm more than pleased with Lucid...

---

### Post by phillw on 2010-02-25
Well, since I decided to make it my "Production Machine" -- Not a murmur of complaint - A bug exists in filezilla for my FTP stuff, but 10.04 and the in-built "generate a **good** bug report" with all the stuff they need seems to be happier (or, they've solved the bug on the bug-reporting system).

I'm real happy with 10.04 alpha 2.9999  ;)

I know you're all real busy with testing, but.. if you have a spare hour, could you please test out the alpha3 of lubuntu, the newest member of the Ubuntu family (Yay, Ubuntu is having a baby :D) - It may be a couple of days behind the main 10.04 alpha3, but we do need it testing. 

I could, at this point say that is more stable than some of things we've been asked to test, but, heck -- that's what testing is all about :D

Pop over to -->  [https://wiki.ubuntu.com/Lubuntu/](https://wiki.ubuntu.com/Lubuntu/)    and check for when the a3 comes out.  

IRC is #lubuntu


Thanks,

Phill.

---

### Post by phillw on 2010-02-25
alpha3 is out --> [https://wiki.ubuntu.com/Lubuntu/](https://wiki.ubuntu.com/Lubuntu/)

Thanks in advance for testing :D

Regards,

Phill.

---

### Post by ranch hand on 2010-02-25
> **phillw said:**
> Well, since I decided to make it my "Production Machine" -- Not a murmur of complaint - A bug exists in filezilla for my FTP stuff, but 10.04 and the in-built "generate a **good** bug report" with all the stuff they need seems to be happier (or, they've solved the bug on the bug-reporting system).

I'm real happy with 10.04 alpha 2.9999  ;)

I know you're all real busy with testing, but.. if you have a spare hour, could you please test out the alpha3 of lubuntu, the newest member of the Ubuntu family (Yay, Ubuntu is having a baby :D) - It may be a couple of days behind the main 10.04 alpha3, but we do need it testing. 

I could, at this point say that is more stable than some of things we've been asked to test, but, heck -- that's what testing is all about :D

Pop over to -->  [https://wiki.ubuntu.com/Lubuntu/](https://wiki.ubuntu.com/Lubuntu/)    and check for when the a3 comes out.  

IRC is #lubuntu


Thanks,

Phill.
That link claims it is up now.   I am going to download the bugger.  I wasn't even going to look for another week for it.  They are working pretty fast on this.

It is more stable because of the lack of plymouth mainly.

Lxdm still seems a little shaky.

---

### Post by katie-xx on 2010-02-25
[SIZE=2][COLOR=Blue]Hmm,
Everything was going so well until tonight :)
First the problems with the Live CD and now .....
Following a few restarts the Plymouth splash doesnt load anymore ....I just get a flashing cursor ... and I have to log in two times to get to my desktop. Thats on my Dell Studio with fresh install of tonight's upgrade.
In addition the shutdown time seems to have increased by quite a few seconds.
Some investigations required here obviously.

Kate[/COLOR][/SIZE]

---

### Post by VMC on 2010-02-25
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]Hmm,
Everything was going so well until tonight :)
First the problems with the Live CD and now .....
Following a few restarts the Plymouth splash doesnt load anymore ....I just get a flashing cursor ... and I have to log in two times to get to my desktop. Thats on my Dell Studio with fresh install of tonight's upgrade.
In addition the shutdown time seems to have increased by quite a few seconds.
Some investigations required here obviously.

Kate[/COLOR][/SIZE]
State your hardware please and those with similar hardware can help.
Also the blinking cursor. does it go away and your presented with a login prompt or do you have to reboot each time?

---

### Post by k3lt01 on 2010-02-25
Well it seems to me that the "going suspiciously well" has come to a screaming halt ;) I'm typing this from Karmic because it is taking Lucid way to long to find web pages and get into them. I waited half an hour just to get into my email gave up went into Karmic and 2 minutes later read and sent emails and now posting here.

The whole boot process seems to be taking ages to. I realise the first one will be a bit slower than usual but every time I try to get into Lucid it seems as though an epoc has past me by. I will try later tonight when I don't have anything pressing to do, not that I am all that busy now but you know what I mean I hope, and see if anything is lagging in the processes department. Maybe some of you kind and informed people will have an idea by then.

---

### Post by k3lt01 on 2010-02-26
Well, when I want to use Lucid I have to be prepared for a long wait. I am using it now and it seems "relatively" ok for the time being. Each time I want to use Lucid I start it up, wait for 20 minutes or so for it to become usable just when the hard drive light stops flickering and I can actually get the mouse to move it logs itself out and restarts back at the log in screen. When I log in the 2nd time it takes its time to be usable but after about 10 minutes it seems to be ok. It has done this 4 times this afternoon.

---

### Post by Lunx on 2010-02-26
How am I supposed to report bugs when nothing is breaking??? ;)

---

### Post by VMC on 2010-02-26
> **Lunx said:**
> How am I supposed to report bugs when nothing is breaking??? ;)
Your not doing it right.

---

### Post by ranch hand on 2010-02-26
> **VMC said:**
> Your not doing it right.
Obviously new to testing if they haven't broken anything yet.

Push the bugger till it breaks.  If it doesn't break be very disappointed.

Have FUN.

---

### Post by phillw on 2010-02-26
Humph... I've given up trying to break 10.04a3 ... mebbie I'll have better luck with lubuntu ;)

Phill.

---

### Post by rixtr66 on 2010-02-26
well i cant seem to break anything in alpha 3?
im set up for audio production and so far everything works.
the only bug ive found,is when installing from the ubuntu software center,i get an error message saying it has to close?but it still continues to install.weird,anyway i will continue to try and break
this sucker,but its running awfully smooth.
Rick :guitar:

---

### Post by phillw on 2010-04-06
Awaits to be moved to testimonials ;-)

No button moving comments, they had no effect on the stability.

Plymouth / nVidea, heck these things happen. Is it 'getting there' ?

But, once you have it working, how stable is it - this is vitally important for an LTS.

Heck, I can't even break Lubuntu after I put a full LAMP server, GIMP, FireFox, compiling libraries, uncle tom cobbly and all.... It's all looking like a one heck of a good LTS to me :-D

A couple of questions, how is 'vanilla' 10.04 going with some of the things it needs, like 
[list]Server: (I cannot break it, has anyone managed it)
RAID: (Oh, let it work this time)
Samba: I am led to believe is now working again (I will have a 'play' with it with XP next week)
[/list]

I'm itchy to send an article into one of the magazines in the UK that I have had articles published in before so as to 'spread the word', so would appreciate if you could provide for the gap in this thread (the people who make the software for where I was keeping a blog managed to delete it & the backup). :(

Rock on that penguin :popcorn:

Regards,

Phill.

---

