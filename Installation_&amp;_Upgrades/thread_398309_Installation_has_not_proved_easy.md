---
title: "Installation has not proved easy"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Gabina on 2007-03-31
:(  I am having a heck of a time.  I started trying to install at about 11:30 this morning.  It's after 8 now.  2 cd's were bad.  One of them got to 73% of the install and then froze, saying there was 464 minutes remaining.

Meanwhile, I used my laptop to download ubuntu again.  I finally get that and get it burned and I try to install using it.

I get the first menu fairly quickly. If I choose install or start.... I get start apparently and not anything even close to looking like an install. And it takes a year and a half.

If I choose start in safe graphics mode (which is how I managed to even start the install that got me to 73%), it takes 3 years.  Each click is a nightmare of waiting.

Please tell me Ubuntu won't be like this once it's loaded. I want to love Linux, I really do.  I don't want to pay Microsoft for another operating system.  And I certainly don't want Vista. 

I was told this would be easy and so far it is anything but.  

Now, on the third try with the new cd, booting to start in safe graphics mode...I hope it will let me successfully install sometime before midnight.

My husband and I had plans to go to a movie tonight.  They are slowly, slowly being ruined.

Cross your fingers that this time it will work, please.

--Gabrielle

---

### Post by Gabina on 2007-03-31
Great. 

I'm getting the same message that I got under start or install, something about gnome and settings such as themes not loading.  Last error message was: Did not receive a reply.

It never asked!

And this is what I got under start or install.  So how in the world do I get it to install?  In my previous attempt, it was 6.06.1 and it had a menu at the top that I could use to start the install. If this (start in safe graphics mode) attempt brings me to the same place as start or install on this 6.10 then I don't know how to start the install!  

It brought up a file browser and had three icons in the upper left: new volume (my removeable drive, I guess), Install (the CD with the supposed install), and examples.  I tried double-clicking Install. I tried single-clicking install. I waited for 15 minutes and NOTHING happened.

I'm going nuts and I'm starting to cuss. It takes a lot of frustration to get me to do that.  Please is anyone out there who can tell me how to get to the install?  The icons are nearly (could be within the next 10 minutes) up on the screen and I'll be the File Browser. If there's no menu at the top, I really don't know where to go.

--Gabrielle

---

### Post by chamberlain2006 on 2007-03-31
You might want to try the Alternate Install CD.  I don't know why your discs would be bad, maybe try at a lower Write Speed (4x maximum).  It will probably be better once you've booted of the HDD though.

---

### Post by Gabina on 2007-03-31
I'm going to scream if I have to download or burn it again and start over.  First let's just see if this Live start will let me get to the point of installation.  I haven't actually gotten to the point of installation with this newly burned CD.  

Presently, I have a yellow screen with two grey bars at the top and bottom. No icons.  Incredibly slow.  Waiting for a menu or icons or the file browser or any sign of life.

--Gabrielle

---

### Post by Gabina on 2007-03-31
Thank God! It has a menu!  Now maybe, just maybe, I can install.

--Gabrielle

---

### Post by chamberlain2006 on 2007-03-31
That's weird, never seen it happen.

---

### Post by aysiu on 2007-03-31
Well, a couple things.

1. Make sure you are burning your CDs correctly by checking their integrity and burning at slow speeds. More details here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

2. The Desktop CD is a live CD (that can also install Ubuntu). The live CD runs out of your computer's RAM and does not affect your hard drive (until you click the **Install** icon on the desktop). If you don't have enough RAM to run the live CD, it will freeze. How much RAM do you have? If you have 256 MB or less, you may want to consider using the Alternate CD instead of the Desktop CD. 256 MB is borderline enough, 512 MB is definitely enough, and 128 MB is definitely not enough.

---

### Post by Gabina on 2007-03-31
Honestly, I can't remember how much RAM I have in this box without rebooting.  Which would make me start this countdown all over again.  But it was enough to run Windows XP. So I am pretty sure it's more than 128MB. Don't know that it's as high as 512MB.  I was told Linux doesn't require as many resources as Windows.  Not sure I believe that anymore.

Presently, I did get the menu and chose Install but have taken a shower between that click and waiting for the install screen to arrive.  It's still not here, but the computer must be doing something because you have to wait a few minutes before the mouse even moves. 

Is there an equivalent to Task Manager in Windows?  Someplace I can see what this computer is doing and maybe why it's bogging down so terribly?

And really the last thing I want to do is download a 4th CD.  That may put Linux off another month with me.  It's been years already since I first wanted to try.

--Gabrielle

---

### Post by aysiu on 2007-03-31
I think you're misunderstanding something here. Ubuntu's Desktop CD does not use more resources than Windows XP. The live CD (also known as the Desktop CD) runs a completely functioning operating system out of your computer's RAM and the CD itself. It does not touch your hard drive. If you can find me a Windows CD that runs a fully functioning Windows environment without touching your computer's hard drive... and at normal speeds, I'll be very surprised. Very, very surprised. After you install Ubuntu *to your hard drive* (not just running a live session out of your computer's RAM), it will run much more quickly.

You're partially right, though--standard Ubuntu or Kubuntu does not necessarily use fewer resources than Windows (probably about the same as Windows), but you can easily customize your Linux installation to use very few resources at all if you have a lightweight window manager. Damn Small Linux, for example, uses a lightweight window manager called Fluxbox, and it manages to run on computers with 16 MB of RAM.

Let me repeat: the Desktop CD runs a **completely fully functioning operating system session** off the CD and your computer's RAM. This is **not** the same as a hard drive installation of Ubuntu--it will be much, much slower.

Here's a little RAM breakdown for you

64 MB - too little for any of the standard *buntus. You would have to use a specialized setup with a lightweight window manager like IceWM or Fluxbox

128 MB - too little to use the Desktop CD to install any of the *buntus. You could use the Alternate CD to install and run any of the *buntus, but Xubuntu would be the best performance

256 MB - sometimes can run the Desktop CD a little too slowly to allow an installation without freezing. The Desktop CD could be run successfully on its own, though, without installing, depending on how many programs you're running at once. Any *buntu would be fine to install using the Alternate CD

512 MB or above - perfect for any situation. You could use the Desktop CD, any of the *buntus, or the Alternate CD

My guess, if you're running XP is that you have at least 256 MB of RAM. If that's the case, I'd definitely use the Alternate CD.

---

### Post by Gabina on 2007-03-31
I think you misunderstand me.

I am not a computer idiot. I know that a live CD does not change anything on the hard drive.  

I am a MSDST, one of the 500 to get that certification.

I just happen to have several computers at home and haven't used this one in a long time and thus don't remember (because I didn't watch when I booted it) how much RAM it has.

CD#1 was bad.  I ran the check CD for errors on my husband's laptop (because it was handy) and it came up with checksum errors.  I had burned that one on Friday.

CD#2 was iffy.  I could boot to live CD on my husband's computer. I could not boot to install on the computer I wanted to install on. I could boot to live, but it took forever.  Then I could start the install.  It stopped at 73%.  You can't say it's because of too little RAM because other evidence would complicate that.  I couldn't even copy files from the CD in Windows.  It would choke up the CD Drive.  On 2 computers. Some of the files were corrupt.  It's probably a miracle it got to 73%

CD #3 was downloaded just a few hours ago.  It should work fine. It's got this far.  But it has still not brought up the install program. I clicked System and then Administration and Install.

Nada.  It's nearly an hour now.

I am, with trepidation, downloading an alternate CD. Why trepidation?  I'm not a computer idiot but I am a complete Linux newbie.  This says for specialist installation. I'm no specialist for any kind of Linux.  Will it be more complicated?  When I did see the installation program (CD#2) it was straightforward.  Will Alternate CD?

I am going to go to a funny movie.  Maybe the laughter will help me not throw this computer out a window and hate Linux forever.  I really do want to love it.  First impression is making it very, very hard.

--Gabrielle

---

### Post by confused57 on 2007-03-31
See the first link in my signature for installing with the Alternate CD, this one:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I actually prefer installing with the Alternate installer, I feel like I have more control over the install process, but that's just me.

---

### Post by aysiu on 2007-03-31
My point wasn't really about the CD affecting the hard drive as more that it wasn't using the hard drive--explaining why it appears to use more resources than Windows.

The Alternate CD isn't scary at all, especially since you are not a computer idiot. It is text-based graphical interface (instead of point-and-click), and it asks you more or less the same questions, but you get a few more options (Install a Server, do an OEM install, etc.).

---

### Post by thecheat on 2007-03-31
The alternate install is actually really easy. You shouldn't have any problems with it at all. 

Good luck!

---

### Post by Gabina on 2007-04-01
Finally got it installed with the alternate CD.  There are still some things I don't understand about Linux though so I'll look in some other forums.  

Thanks.

--Gabrielle

---

### Post by denverreynolds on 2007-04-02
Just wanted to say nice write-ups in here by some more great ubunto users. I cant tell you how lost I would have been without the community last month. Days,,,,days to get everything working LoL!!!!! But I made sure to record ALL the instructions and links. Plus I backed up my whole install onto my external drive so that if I do anything stupid i can just copy it.

Thanks again!

---

### Post by unisol on 2007-04-02
altrnate install cd is a good idea. how about your system specs?

---

