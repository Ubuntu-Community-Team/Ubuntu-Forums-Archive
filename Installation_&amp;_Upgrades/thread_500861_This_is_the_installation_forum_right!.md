---
title: "This is the installation forum right?!"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2007-07-14
Okay well someone (seing as this is the installation help forum) please respond to this post:
[http://ubuntuforums.org/showthread.php?t=499694](http://ubuntuforums.org/showthread.php?t=499694)
I ahve been trying to fix this for a while no, and evertime its bumped noone replys. This forum is full of mods right so there should be some sort of reply. If I am posting this in the wrong section please tell we were I am suposed to put this post?

---

### Post by merlinus on 2007-07-14
Ya know, over a day ago I asked you to post the output of:

```

sudo fdisk -l

```so that I, and others, might see how your disk(s) is/are partitioned.

You never responded.

So quityerbitchin and get with the program!

And whilst you are at it, how about hardware specs, how you partitioned your vista install, etc.

-merlin

---

### Post by Jeremywilms on 2007-07-14
I don't know what that is, I never said I was a  computer tech guy, i'm a java programmer, wich has nothing to do with what you were saying. Now If someone could please answer my question.

---

### Post by Jeremywilms on 2007-07-14
[IMG]http://www.freewebs.com/jeremywilms/Screenshot%2D1.png[/IMG]
my output is nothing.

---

### Post by merlinus on 2007-07-14
sudo fdisk -l

(l is a lowercase L, not the number 1)

Also, i see in your original thread that someone suggested you may need to restore the mbr.

Have you tried SuperGrub?

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by confused57 on 2007-07-14
```
sudo fdisk -l
```
-l is a lowercase "L"

If you have a Vista install DVD, you should be able to restore your mbr...I think there is a Startup repair option.

When you were installing Ubuntu, how long did you wait when the installation stalled?  Also, as Merlinus mentioned, the more you can tell us about your system, the better chance someone might be able to offer a solution.

Added:  Merlinus beat me to it.

---

### Post by Jeremywilms on 2007-07-15
=P the problem is...I don't quite want duel boot I want my main OS working again, then I will try to install duel boot again. Anyway here id the results.

[IMG]http://www.freewebs.com/jeremy6996/Screenshot.png[/IMG]

---

### Post by merlinus on 2007-07-15
If you do not have your original vista dvd, which has a restore option, then SuperGrub will allow you to fix the mbr (master boot record).

Check the link in my last post.  The page also has directions for doing this.

From the output of sudo fdisk -l, all that is left on your hdd is your windows partition.

-merlin

---

### Post by Jeremywilms on 2007-07-16
Okay, I put the CD in and I have the ISO in it, and the extracted ISO file. Though it says on the computer boot 

"Reboot and Select proper Boot device or insert Boot Media in selected Boot device"

The thing is, I made my computer only boot from the CD.Though when Input the CD in my CD Drive, nothing happend. Well i got that message.

---

### Post by merlinus on 2007-07-16
What do you mean by:

the extracted .iso file?

Did you burn the cd as a disk image?  Your burner software should give you this option.

If you extracted the files before burning, that is your problem, and from the error message, it would seem so.

-merlin

---

### Post by Pumalite on 2007-07-16
A java programmer ???

---

### Post by Jeremywilms on 2007-07-16
> **merlinus said:**
> What do you mean by:

the extracted .iso file?

Did you burn the cd as a disk image?  Your burner software should give you this option.

If you extracted the files before burning, that is your problem, and from the error message, it would seem so.

-merlin

Well....I burnd the ISO by it-self and it did not launch. So I put the extracted Files too. and got the same results.

> **Pumalite said:**
> A java programmer ???
You do know what java is. Right?

---

### Post by Pumalite on 2007-07-16
Do you know what I.Q. is?

---

### Post by Jeremywilms on 2007-07-16
> **Pumalite said:**
> Do you know what I.Q. is?

I'm not looking for a flame war.

Someone answer my quetion please.

---

### Post by merlinus on 2007-07-16
Did your burn the .iso as a disk image and NOT as a data disk?  If you did, and since it will not boot your computer, it is one of three things:

1.  The cd has errors.  Perhaps it was burned too fast.

2.  The ,iso has errors,  You can test this by using the checksums available at the download site, and comparing them with yours.

3.  Your cd drive has defects.

-merlin

---

### Post by Jeremywilms on 2007-07-16
Xd well I drag and droped the ISO. How do I burn the iso as an image?

---

### Post by raul_ on 2007-07-16
Most CD Burning applications have an option called "Burn Image (.iso) file"

But I don't get it, your problem shouldn't be that, because you can boot with the Live CD as you said in the other thread.

The problem about the installation hanging is probably due to cd errors. You should check the CD for errors, and if there are any, burn the CD again at a lower speed, maybe 4x

---

### Post by Jeremywilms on 2007-07-16
Okay maby i'm burning the wrong file. Could someone give me a 100% direct download link?

---

### Post by raul_ on 2007-07-16
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Jeremywilms on 2007-07-17
I need the link to super grub.

---

### Post by confused57 on 2007-07-17
> **Jeremywilms said:**
> I need the link to super grub.
See the section "Where to get your Super Grub Disk":
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Jeremywilms on 2007-07-17
Yay I installed the ISO on the CD, then I tried it as a CD image. Its not laucnhing

---

### Post by Jeremywilms on 2007-07-18
Does no one have an explination. This is exactly what I am doing,
1.  Burning to the CD as an ISO with XP.
2.  Restarting the computer disabling my harddrive boot,k and enabling my CD boot.
3.Restart me computer with the CD in.
4. Does'nt work.

Can someone tell me the exact size this is supposed to be, so I know if I keep corrupting it.

---

### Post by raul_ on 2007-07-18
Again, how did you burn the ISO file? It's not supposed to be one big file in the CD.

---

### Post by Jeremywilms on 2007-07-18
> **raul_ said:**
> Again, how did you burn the ISO file? It's not supposed to be one big file in the CD.

Well I First tried the ISO burned  onto the CD( as one big file)
Then I tried it as an extracted ISO.

---

### Post by LowSky on 2007-07-18
How come all the programmers I meet know nothing about computers except their college learned programming language?



anyway...

do you have nero?

that has an option to make an iso

also make sure your computer is booting from the DVD-ROM in your bios.

BTW try a Google search or the Search featers of this website before asking questions

---

### Post by raul_ on 2007-07-18
Being a writer doesn't mean one knows how the book is printed or how paper is made

---

### Post by merlinus on 2007-07-18
> **raul_ said:**
> Being a writer doesn't mean one knows how the book is printed or how paper is made

Maybe not, but a writer certainly needs to know how to use the tools of the trade, so to speak, e.g. pen and/or computer word processor.

A wannabe computer programmer should learn how to use the tools similarly.

Also, jeremy has been instructed in many posts in several of his threads exactly how to burn an .iso, and even how to checksum it.

I am beginning to believe that he is nothing more than a troll.

-merlin

---

### Post by Pumalite on 2007-07-18
I agree.

---

### Post by raul_ on 2007-07-18
> **merlinus said:**
> Maybe not, but a writer certainly needs to know how to use the tools of the trade, so to speak, e.g. pen and/or computer word processor.

A wannabe computer programmer should learn how to use the tools similarly.

Also, jeremy has been instructed in many posts in several of his threads exactly how to burn an .iso, and even how to checksum it.

I am beginning to believe that he is nothing more than a troll.

-merlin

About the first part, a programmer's tool is an editor/IDE ;)

about the second part I agree

---

### Post by Jeremywilms on 2007-07-20
So does anyone know whats wrong?

*edit* 
okay i'll see if it works tommorow i'm quite busy right now.

P.S Te only boot option I have enabled is from the CD

---

### Post by Jeremywilms on 2007-07-20
> **merlinus said:**
> Maybe not, but a writer certainly needs to know how to use the tools of the trade, so to speak, e.g. pen and/or computer word processor.

A wannabe computer programmer should learn how to use the tools similarly.

Also, jeremy has been instructed in many posts in several of his threads exactly how to burn an .iso, and even how to checksum it.

I am beginning to believe that he is nothing more than a troll.

-merlin
In the many replys that I have gotten I have followed them all the way, What makes you think I am a 'wannabe programmer', and a programmer has 3 buttons he constantly uses, All I know is that I press the compiler button that uses the jdk I installed, And I press the run button to run. And that it is comiled into a readable language for the computer. In a java class they do not teach you how to burn a CD. Or set your bios to boot from the CD.  I don't even know what bios are. 



I burned it again and this is a full screenshot of what my CD contains. I'm burning the file on this computer, then puting it in the other.

[IMG]http://http://www.freewebs.com/jeremy6996/aaaaaaaaaaaa.jpg[/IMG]
For some reason the image is not loading click [Here]("http://www.freewebs.com/jeremy6996/aaaaaaaaaaaa.jpg")

---

### Post by Jeremywilms on 2007-07-21
Could I not just use a diffrent program like SuperGrub. Any suggestions? because the ISO is burned correctly.

---

### Post by raul_ on 2007-07-21
Again, I only see one big file on the CD. It's not supposed to.

[ Install this]("http://www.magiciso.com/")

And then 

[This]("http://www.magiciso.com/tutorials/miso-burnwin.htm")

---

### Post by Jeremywilms on 2007-07-31
Sorry for late reply, i'll give it a shot.

---

### Post by Shadows_Fall on 2007-07-31
Ok step one is to download the .iso, which you've done,
so step two is to download the infra recorder, which is found here, [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Scroll down, the download link is above the screenshot, next
install it, and run it. Click the actions menu, and select burn image.
Then select your .iso file, and hit ok, then it'll burn the .iso to a disk,
as an image.

Then just drop the cd into whatever and install.

Hope this helps.

---

