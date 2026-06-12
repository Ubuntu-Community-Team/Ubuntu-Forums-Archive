---
title: "blank screen when trying to boot from disk"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by metalhead8888888 on 2007-08-02
i have burn an image to a disk at 4x but whenever i try to boot from the disk it doesn't even get to the selection screen it just goes to a blank screen. My computer is a nine year old computer intel celeron 400MHz, 384 MB of memory, it's an etower 400i. any help would be appreciated.

---

### Post by dabl on 2007-08-02
2 questions:

1. Are you sure a bootable CD will boot in that PC?

2. Did you check the md5 checksum on the downloaded file that you burned to the CD?

:)

---

### Post by metalhead8888888 on 2007-08-02
yes a bootable cd will work on my computer and i don't know what you mean by the second question i got the download from ubuntu.com.

---

### Post by dannyboy79 on 2007-08-02
> **metalhead8888888 said:**
> yes a bootable cd will work on my computer and i don't know what you mean by the second question i got the download from ubuntu.com.

iso images normally are created with or have a md5 hash. so that after you download it, to make sure you got it downloaded correctly, you check it's md5 hash against what Ubuntu documented it was on it's website.

most likely that's fine. I am guessing it's a video card issue. did you try to boot into safe vga mode? also, what speed did you use to burn it, use the slowest speed always, this will ensure a good burn.

---

### Post by metalhead8888888 on 2007-08-02
i burned it at 4x but i can go to 2x and my video card is a rage 2c and it is built in.

---

### Post by dannyboy79 on 2007-08-02
try to add this at the end of your boot lines within your menu.lst located within /boot/grub/

nosplash vga=791

so an example line would be this:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro quiet nosplash vga=791

---

### Post by metalhead8888888 on 2007-08-02
their isn't a boot or grub folder should i go with xubuntu instead.

---

### Post by dannyboy79 on 2007-08-02
huh? are you saying that you have a blank screen when booting from livecd or from the hard drive?

My instructions assumed when you said disk, you meant a disk (hard **disk**) not a disc (livecd)

So please clarify and I can help. If you don't have a /boot/grub/ folder, than that means that your install completely failed and I am not sure what you did.

Gnome should work but it'll be slow. xubuntu will give you much better performance but your issue will be the same. It has to do with your rage card I am almost certain.

I had the same problem with my ATI AIW 9800 Pro. Here's the thread I documented my experience: [http://ubuntuforums.org/showthread.php?t=389980](http://ubuntuforums.org/showthread.php?t=389980)

---

### Post by metalhead8888888 on 2007-08-02
sorry but i am using a live cd

---

### Post by dannyboy79 on 2007-08-02
> **metalhead8888888 said:**
> sorry but i am using a live cd

well, help is still in that same link I already provided you. It deals with changing the boot parameters when booting the livecd by using break=bottom, and changing the xorg.conf that gets loaded etc etc. Good luck. it worked for me and I documented everything for this very reason.

---

### Post by metalhead8888888 on 2007-08-02
how would i change parameters i need you to explain more.:confused:

---

### Post by dannyboy79 on 2007-08-02
it's all the link I have already given you. 

basically when you're presented with the very first menu within the livecd, you hit F6 and that'll bring you to a grub menu, this is all in the link I provided along with this link [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

---

### Post by metalhead8888888 on 2007-08-02
i can't even get to that screen before it goes blank. on the screen it shows the computer looking through the cd-rom for the program then it goes to switch screens and goes blank instead of showing that screen.

---

### Post by dannyboy79 on 2007-08-02
> **metalhead8888888 said:**
> on the screen it shows the computer looking through the cd-rom for the program then it goes to switch screens and goes blank instead of showing that screen.
please explain how you know that the computer is looking thru the cd-rom for a program? If this is the case and you clearly set your bios to boot from a cd, then I suggets you reburn AFTER you verify the md5hash of the iso that you downloaded.

---

### Post by metalhead8888888 on 2007-08-02
it says on the bottom of the screen that it is looking for a boot file for the cd-rom and floppy drives if there is anything in them then goes to a light blank screen. the md5sum is just a bunch of computer talk and i can't really read that. it only goes to that screen when the cd is in.

---

### Post by dannyboy79 on 2007-08-02
> **metalhead8888888 said:**
> it says on the bottom of the screen that it is looking for the boot file then goes to a light blank screen and the md5sum is just a bunch of computer talk and i can't really read that. it only goes to that screen when the cd is in.

are you saying that you're not willing to check the md5sum of the iso you downloaded? if so, than I can't suggest any other help because without a properly downloaded iso, then burned properly, there's not much more to touble shoot as these are the first things to check. it sounds like, from what you're saying, that the computer does start to boot from the cd but it can't find the kernel to load. You should have enough RAM but maybe not, it tries to load the entire livecd into RAM and run it from there and if you don't have enough ram, I am not sure if there's some kind of error or if this is what happens. Try out Xubuntu.

Also, to be honest with you, if you're not going to try to learn how to check a md5sum, then how will you attempt to learn linux? I am merely trying to keep it real.

Here's a guide for checking md5sum's. (everything can be learned using google)
[http://mandrivausers.org/index.php?showtopic=4638](http://mandrivausers.org/index.php?showtopic=4638)

(NOTE: you'll want to get the Ubuntu md5sum's from wherever you download it from, it's normally posted with it somewhere) If it's not, here's a list of them for Feisty: 50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

---

### Post by metalhead8888888 on 2007-08-02
it's not that i am not willing to it's that i am not that good with that kind of stuff i don't understand it. you've confused me with the checking the md5sum the iso i downloaded though is ubuntu-7.04-desktop-i386.iso.

---

### Post by dannyboy79 on 2007-08-02
do you understand linux? I am guessing not but you want to try it because it's free right? Well that shouldn't be the only reason because being a newbie into linux, I will almost guarentee you some type of trouble where you'll have to learn how to fix it. Like I said, if you don't want to even attempt to learn how to check a md5sum, then I would suggest paying $90 for WinXP Home and use that.

Did you even look at the link I provided. It's not even hard, you download a .zip, extract it, bring up a dos prompt in winbloz, run it against the .iso and you get a number, now compare that number to the numbers I posted (if you downloaded Feisty) and then we can examine the next thing. it's not hard, it's only as hard as you're making it on yourself.

---

### Post by metalhead8888888 on 2007-08-02
i asked for people to help me not criticize me and this is my first time messing with iso's and images so sorry for begin so slow at this.

---

### Post by dannyboy79 on 2007-08-02
> **metalhead8888888 said:**
> i asked for people to help me not criticize me and this is my first time messing with iso's and images so sorry for begin so slow at this.
there is in no way shape or form an insult anywhere in my last post. I am trying to help you and the troubleshooting we need to do you're saying that you can't do it but I know you can because anyone can do it. If you can read, follow instructions, see, type on the keyboard then you can do it.

I understand that this is your first time with an iso and checking it's md5sum. That's why I pasted a link instead of just saying, check it's md5sum. People can't help you if you're not willing to help yourself.

---

### Post by diatribe on 2007-08-02
> **dannyboy79 said:**
> there is in no way shape or form an insult anywhere in my last post. I am trying to help you and the troubleshooting we need to do you're saying that you can't do it but I know you can because anyone can do it. If you can read, follow instructions, see, type on the keyboard then you can do it.

I understand that this is your first time with an iso and checking it's md5sum. That's why I pasted a link instead of just saying, check it's md5sum. People can't help you if you're not willing to help yourself.

Indeed he is not being insulting but you are not allowing him to help you either.

---

### Post by metalhead8888888 on 2007-08-02
i am trying to figure the md5sum file thing with the website given at the moment

---

### Post by metalhead8888888 on 2007-08-02
i am trying to figure out how to run the md5sum program from the web site given but i don't get i put it in the folder i downloaded the iso to and ran it but it just brings up a window then closes it. i do think that the iso is bad though.

---

### Post by dannyboy79 on 2007-08-03
> **diatribe said:**
> Indeed he is not being insulting but you are not allowing him to help you either.

wow, thanks for chiming in. You can take over and help at any point instead of providing a needless comment.

---

### Post by metalhead8888888 on 2007-08-03
there was no problem with the download on my computer can't handle the newer one but it can handle 6.06 i'm thinking it is because of my old bios but there isn't any update for it so basically you just insalted me for not being a pro at computers and wasted my time doing useless things that was too complicated so that makes you not very good at helping people. i also stated how old my computer and major things that are required to run things so apperently you aren't a pro at lunix either because you should of know my computer wasn't compatable.

---

### Post by dannyboy79 on 2007-08-05
if your dapper runs on your computer than your older computer certainly can run on Feisty and even Gutsy. It's newer computers that the kernel sometimes isn't compatible.

There are many boot options you could've tried before throwing in the towel but that's your choice. You even stated it yourself that you thought it was a bad iso so you should've downloaded again, checked the md5sum and burned it very slow and tried it out. I never said I was an expert in Ubuntu let alone linux so for you to assume that is on you not me.

Many newbies often take the easy way out and either go back to Winbloz or do whatever easiest, it appears that you have done the same and that's fine. Good luck with everything.

---

### Post by anewguy on 2007-08-06
I'm just a beginner myself, so I'll try to explain something the best I can.  The md5 sum stuff is still needed, even if you downloaded from Ubuntu and the download completed.  This is a way of verifying that no errors where introduced in the download file while it was being downloaded - like say noise on the internet connection, etc..  All they are asking you to do is do this to verify what you downloaded is ok.  If you need a step-by-step for the md5 stuff, just say that you don't know how to do that and could someone give you some instructions - you'll probably get them.

If you think 7.04 is too big for your memory, try looking at xubuntu - it's sort of a "shrunk down" version of Ubuntu.  My understanding is that it is intended for older machines that don't have the cpu and memory needed for "full" Ubuntu.

Good luck!:)


EDIT:  To others replying to this post:  I understand your frustration, but do try to remember this is the "Absolute Beginners Forum".  Also, with the push in the magazines, etc., building up Ubuntu, people are going to come here to try Ubuntu, people who aren't in the least little bit technical or have a desire to be.   These people have probably gotten Windows preinstalled on their PC and they never had to do anything to make it work.  They are looking for the same experience here, and some expect it given the push for Ubuntu to be a desktop OS replacement.  The old ways of thinking, that everyone is going to have problems and they need to learn how to search and do at least some of the work themselves just won't work for those people.  A more realistic "welcome" to Ubuntu, and Linux in general, might be to say "yes it's a free OS for your PC.  Yes it can do most (don't kill me here - there are some things Linux really just doesn't do in a way comparable to Windows) things that Windows can.  Please be advised that you will probably run in to some problems either installing or getting everything to work after installing.  Currently that is the nature of Linux, not just Ubuntu.  You should, however, always be able to find the help you need here on the Ubuntu forums".  This is more realistic to the status of things.  Some people coming over to try Ubuntu don't know that, and they think they should be able to just have it on their machine like Windows.  We may not like that, but we have to expect and respect that. ;)

---

