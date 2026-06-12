---
title: "Downloaded to cd but cd won't boot"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by Cam72 on 2008-08-22
I just dowloaded the latest version of Ubutu and it's curently on a cd-r but it will NOT boot.  Before coming here i looked up how to change boot order and i did but it still won't work.  If anyone could help this Newbie new user i'd be greatly apreciative.

---

### Post by insane_alien on 2008-08-22
did you write it to disk as data or as a CD image?

---

### Post by niyonk on 2008-08-22
hi, :)

Do you have any other bootable CD you can test with?
Or how exactly did you burn the CD and what program did you use?

---

### Post by Cam72 on 2008-08-22
As a Image

---

### Post by Cam72 on 2008-08-22
I used Sonic Record now but i'm running windows right now so i dont have another bootable cd

---

### Post by Cam72 on 2008-08-22
any advice?

---

### Post by niyonk on 2008-08-22
ok, 
When you boot your pc, do you hear a noise as if it is trying to check if the CD is bootable.
And also do you see a black screen for few seconds and a blinking cursor while this is happening.

(I am assuming you selected something like...'Burn an ISO Image')

or check if the image you downloaded is not corrupted using [this link]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Cam72 on 2008-08-22
what you describe is exactly what happens but then it cancels and loads windows

---

### Post by Cam72 on 2008-08-22
i did burn an iso image - is that the wrong way?

---

### Post by Cam72 on 2008-08-22
by the way, i dowloaded and compared hashes and stuff but there the same

---

### Post by Cam72 on 2008-08-22
useing that link

---

### Post by niyonk on 2008-08-22
What way to you mean exactly...because there is burning an iso to cd and there is burning an iso file to CD

ok, not to confuse you more you might want to look at [this]("http://www.uab.edu/it/question-answer/other/iso_cd.php") the last part...:)

---

### Post by Too Late on 2008-08-22
Can you read the contents of that disc in Windows?

---

### Post by Cam72 on 2008-08-22
no it just opens sonic record now

---

### Post by gjoellee on 2008-08-22
Sometimes if you have two floppy disks, you have to use the one you normally don't use, like for me Ubuntu CD's  doesn't even get detected in the normal floppy, so I have to use the one that is actually made for burning CD's

---

### Post by Cam72 on 2008-08-22
thats wht i did, burn iso to cd but i used sonic instead of that other thin on the link

---

### Post by Cam72 on 2008-08-22
floppy disk? but anyways it dose reconize that ubuntu is on the cd in windows it just wont ope it of course

---

### Post by Too Late on 2008-08-22
Go to My Computer and right-click that CD and select properties. Tell us what do you see? How much used space, how much files etc.

---

### Post by Cam72 on 2008-08-22
ok hold on

---

### Post by SkonesMickLoud on 2008-08-22
What speed did you burn the CD at?

Typically, you want to burn .iso files at 4x or less.

---

### Post by Cam72 on 2008-08-22
it says there's no free space wich is odd because i know there is,  it says the file system is CDFS, and it says the size of Ubuntu is 694mb.  The reason it says no free space is because it's a cd-r not cd-rw actually

---

### Post by Cam72 on 2008-08-22
well i dont know but it took about 30 min

---

### Post by Too Late on 2008-08-22
> **SkonesMickLoud said:**
> What speed did you burn the CD at?

Typically, you want to burn .iso files at 4x or less.
IMO, that's an urban legend. I always burn my discs at max speed and I've never had problems with them. In fact, another urban legend says that burning discs at too slow speed could cause them to burn "away" (I mean, the rays go through the disc).

---

### Post by Cam72 on 2008-08-22
ya thats what i thought, just urban legends, but burn through the disk thats rediculous

---

### Post by Cam72 on 2008-08-22
anything?

---

### Post by Too Late on 2008-08-22
> **Cam72 said:**
> it says there's no free space wich is odd because i know there is,  it says the file system is CDFS, and it says the size of Ubuntu is 694mb.  The reason it says no free space is because it's a cd-r not cd-rw actually
Well, that indicates that you've done everything right. It could be a hardware issue. I have one very old CD drive which can't boot anymore.

edit: So what will you see when you double-click that disc?

---

### Post by Cam72 on 2008-08-22
so what should i do to fix the hardware or what ever else?

---

### Post by Cam72 on 2008-08-22
didnt read end part:  but it opens sonic record now and also just to let you know i burn and rip d=cds all the time and i juts had my cd drive replaced about 6 months ago when my motherboard crashed

---

### Post by Cam72 on 2008-08-22
i`mean when i click on the drive it brings me to the iso image file wich is ubuntu

---

### Post by Cam72 on 2008-08-22
when i click iso it opens sonic now

---

### Post by Too Late on 2008-08-22
OK, **you shouldn't see any iso files in your disc**. So you have NOT burned it correctly. You have burned that iso file as data. You should burn that as an image. If you can't do that with your current program, please try another burning program.

---

### Post by unca.paka on 2008-08-22
Looks like it just burned the .iso to the disc, and didnt make it bootable. If Sonic wont do it, just grab the demo of MagicISO, pretty easy to use.

---

### Post by Cam72 on 2008-08-22
thank you both, i'm going to try magiciso and hopefully it will work!


I'll make this ques resolved if it dose keep an eye out

---

### Post by Cam72 on 2008-08-22
Unca, how to i use magiciso to make it bootable? i'm re-downloading ubuntu right now

---

### Post by Too Late on 2008-08-22
No need to re-download. You could have used that same iso file that you accidentally burned to that disc (as data).

---

### Post by Cam72 on 2008-08-22
where would it be on my comp? i looked but couldnt find it

---

### Post by Too Late on 2008-08-22
It's on that disc you already burned.

---

### Post by Cam72 on 2008-08-22
yes but how do i re burn that

---

### Post by Cam72 on 2008-08-22
and on the cd its a a data file isnt it? so it wont burn it as iso

---

### Post by Too Late on 2008-08-22
Of course you can't burn a file from disc to another disc, unless you have multiple optical drives. So just copy that iso file from your (already burned) disc to your hard drive. Then burn that iso image (which is a data file) to a disc, and be sure to burn that file as an image, not as data.

---

### Post by Cam72 on 2008-08-22
ok but it will be an image file on cd when i burn it from my hard drive as long as i'm useing magiciso?

---

### Post by niyonk on 2008-08-22
that's what i've been trying to tell you my friend...:)

You burned the ISO file itself..not Burned the ISO to the CD.

It doesn't matter what program you use as long as you burn the ISO to cd not the file lol
Actually you might want to look at the link I posted earlier on...on the last part.

Good Luck! ;)

---

