---
title: "Scared of upgrading my Ubuntu install..."
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by maximo1010 on 2011-04-28
Well, so I'm wanting to upgrade to 11.04, but I'm extremely scared of breaking my installation. First of all, I have all that experimental Compiz bling installed, does it break anything with Natty's Compiz? It obviously won't work because Natty uses 0.9 while Maverick uses 0.8, but hey, I don't want any dummy plugins or anything. Also, these plugins are way too cool to miss (I just installed them and now I can't live without the extra eye-candy). And what's with my awkward startup settings? I have a compiz --replace --loose-binding command in there and many disabled docks that, in KDE, all launch simultaneously (including Compiz, which renders everything unusable) and completely $cr&#8364;w the desktop (I stopped caring about KDE now). Also, my setup feels like my computer's going to blow up any minute while upgrading because of too much dull packages, including gnome-shell which I don't use after all. My computer is, in terms of packages, a complete junkyard! So, is it safe to upgrade with this setup, if yes, tell me the recommended way to do this (CD, update manager?) or if not, how do I scrap that from my updates forever? It's so annoying! By the way, will the upgrade also ruin KDE?

---

### Post by maximo1010 on 2011-04-29
Bump!

---

### Post by 23dornot23d on 2011-04-29
Try it from s Live CD first ..... make sure it is what you want ......

Then if it is ..........


Make room for it and Load it into its own partition and try it ...... that way .....
then you will have both ....... always create a separate /home too ...... that way things
can be done much less painfully - if you decide to upgrade or change it in the future ...........

---

### Post by maximo1010 on 2011-04-29
> **23dornot23d said:**
> Try it from s Live CD first ..... make sure it is what you want ......

Then if it is ..........


Make room for it and Load it into its own partition and try it ...... that way .....
then you will have both ....... always create a separate /home too ...... that way things
can be done much less painfully - if you decide to upgrade or change it in the future ...........
I know what it is like, and I like it. However, what's with /boot and swap and all that stuff? And I was actually asking if it works with my ridiculous setup or not.

---

### Post by Dutch70 on 2011-04-29
Many of your questions are answered here.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by maximo1010 on 2011-04-29
> **Dutch70 said:**
> Many of your questions are answered here.
[[COLOR=Red]http://ubuntuforums.org/showthread.php?t=1580857[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

How will Compiz react? How will Natty react with my goofy startup settings? What will happen to my KDE install?
And I have already read this post, nothing at all is answered. So how can I finally tell it to get that update's dirty fingers off my updates until I've solved my questions?

---

### Post by flybyspam on 2011-04-29
If you have compiz configured...you like it....and it works....don't upgrade!   I "foolishly," trusted that the upgrade would only contain a few minor irritating changes...and i'm very sorry for it.  11.04 appears to be trying to appeal to hand-held devices menu layout.  It doesn't have the menu's that you're used to......UNITY is a lame attempt to "provide you," with what it thinks you're looking for (very similar to windows personalized menu's)...in order to "provide you," with less configurable windows  and menu management.

I had virtual-box running with several os's, encrypted hard drives, and compiz working perfectly.  Now i'm opening everything command line out of pure hatred for UNITY.    apt-get purge unity.

   Ubuntu WAS a pretty good desktop OS.  It a I'm sick of worthless "time-wasting," changes ( i.e. moving the windows resize buttons) every time an upgrade comes out.   It would have been nice if more time were spent cleaning up script redundancies and eliminating functions that don't work anymore (i.e. themes).

I know that there's going to be some response to this like.  "all you have to do to use a different windows manager is.........[some path to an obscure setting in a redundant/changed/nested script]."  

 Luckily I'm a Unix admin and I have the good fortune to be able to use the command line.  It's less trouble to learn the locations of the program locations and links than playing around with another set of menu's.  Which means that I might as well install a lighter weight distro anyway. 

End of rant...

Bottom line.....don't  upgrade if your system is working.

---

### Post by 23dornot23d on 2011-04-30
> 
I  know what it is like, and I like it. 

                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10739472")                                                                                         [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=10739472")

Good then install it in a separate partition alongside your existing version ..... 
( Backup all your important things first though - cut down all chances of losing things )

How big is your hard drive .... how much free space is there on it ...... could you put 10 to 20 gig aside to test it in ......

You will find out all the questions that you want to know ..... and if it does not work properly ..... you will still have your existing system to dual boot into .....

> 
However, what's with /boot and  swap and all that stuff? 


**[COLOR=Red][/boot]("http://www.linuxquestions.org/questions/linux-general-1/boot-separate-partition-541035/")[/COLOR]** ...... an area set aside just specifically to boot from ......

swap and area set aside to use like an overflow/swap area for when your computers memory needs to use it .....

also the one that can be more important is 

/home

This is like your home ..... you keep all your nice bits and bobs in here desktop settings etc .....
and even when you upgrade ....... your bits and bobs and settings remain reasonably safe
in your /home ...... (as long as you[COLOR=Red]** do not**[/COLOR] format it when installing a new system you just choose it and highlight it as /home to your new system )

This is then kept separate while in a separate part of the disk - the system is being set up and this part is being used to put the System files onto its indicated by a backslash ( / )

/

or root ....... (partition) area on the disk put aside for all the System files to go and hopefully operate from ....... if it all loads ok and it correctly picks up and identifies your hardware ... for use.

> 
And I was actually asking if it works with my  ridiculous setup or not.
The only way to find that out try it as I said ........... as I cannot answer this one ....
and I doubt anyone else could 100% 
( without of course they have the exact same setup that you have - "but I do not" ) 


If you need an answer try it as I said and do it the safest way possible ..... always backup your valuable data first  ...... there is always a slight risk involved ..... power can go off /
lightning can strike / a fuse could blow ..... :confused:

---

### Post by ratcheer on 2011-04-30
1) Get Clonezilla

2) Run Clonezilla to make a full image of your disk drive

3) Upgrade to Natty before making any other changes

Now, there's nothing to be afraid of. If it tears up your system, you can use Clonezilla to put things back exactly the way they were.

Tim

---

### Post by technine on 2011-04-30
I will advice you not to install 11.04. I really regret doing so. From a fully working 10.10 to a non-working 11.04. Sooo many problems, everything between no maximize/ minimize toolbar, compiz starting and stopping at random, to not being able to remove file-leftovers in synaptic, to programs not starting half of the time (programs like Gimp, Virtualbox, Firefox, Thunderbird... and several more!) Error-message when i try to install different deb-packages. Not being able to install programs. Programs that starts but is not working properly (koverartist..) And i did a clean install of 11.04, on two pc's, with similar problems (didn't use Unity, i used Ubuntu classic/ Gnome). They must have really rushed this out!? There were more errors than these, and after 1.5 days of struggling i went back to 10.10. Now i'm happy to have a fully working pc again. I will wait a couple of months before i try 11.04 again to see if some of the errors have been sorted out..

---

### Post by markymark64 on 2011-04-30
Yes, I encourage you to hold off as well. The next upgrade will be coming out in October. Testing starts in June. I think Ubuntu made a huge mistake with this latest O.S. and I'm sure they're reading all of the reactions to upgrades as well as issues with displays and broken installs. The one thing I really would like them to do is to create an option when you're doing an upgrade to pick your profile. It would be nice if the upgrade could see your profile so that it doesn't force you to create a new user name all over again. This is so frustrating. I'm thankful I had everything backed up before upgrading because 11.04 hosed my desktop and I could barely boot up to the windows partition. I lost all of my menus and didn't have a working desktop. 

So, if everything is working don't break it. If 10.10 is working for you don't break it by installing 11.04. One guy on this forum already figured out he'd have to upgrade two video cards in two separate pc's and 11.04 would cost him about $140 after all was said and done. Yes, the latest version demands a lot of memory from your video drivers and it will steal from your swap if your video card doesn't have enough memory. That's one of the biggest problems with 11.04.

---

### Post by Dutch70 on 2011-04-30
No, they didn't make a mistake. This happens every 6 months, as it will happen again when the next release comes out in Oct. As a matter of fact, it's likely to be worse, because there will be no Ubuntu Classic to login to. Although people will be more used to Unity by then.

No, the developers do not come here to read our post. If you want to get something to them...file a bug report!

There is **absolutely nothing** wrong with 11.04 that doesn't happen with every new release. That is why everyone that is new to Ubuntu is usually advised to wait about 2 months after the release date to install it. Also, then you don't have a bunch of people posting false information about it when they don't know what they're talking about.

When the OS is in alpha & beta versions, only the people testing to help out are really filing bug reports. That's all the developers have to work with. When it is actually released. There are a lot more people using it on a lot of different hardware so the devs get more input than ever. Give it a couple months. 

The ONLY difference with this version is it uses Unity, and people are not used to it.

---

### Post by alguin2 on 2011-04-30
While the Natty kernel at its core may be good, the accompanying Unity look and feel is a piece of crap.

---

### Post by Dutch70 on 2011-05-01
> **alguin2 said:**
> While the Natty kernel at its core may be good, the accompanying Unity look and feel is a piece of crap.

Obviously the devs knew that some people would feel that way. That's why they included Ubuntu Classic on the login screen. 
I'm still undecided right now, and I'm going to give it what I think is a fair amount of time.

---

### Post by Dale61 on 2011-05-01
If you can fight the urge to upgrade, do so until you start reading posts about everything finally working as it should.  I was going to wait a week or so, and read up in the mean time, but curiosity got the better of me and I'm now regretting my impatience.

So, wait a couple of weeks, but keep monitoring these boards.

---

### Post by Dimarchi on 2011-05-01
Lots of wise words in this thread for you.

If you would like to replicate your current compiz setup in Natty, I am probably very much correct in saying that it will *not* work. Do not upgrade. Especially do not upgrade.

If you wish to have Natty, nevertheless, and you have space for it install it side by side with your 10.10 installation. Just make sure it does not share a thing with your current setup ( /home comes to mind).

Still, the best advice is to wait. Natty is...how should I put it...not quite Gnome, and not quite Unity, either. It is on the way to Unity but has not reached that far, yet. Natty is sort of a showcase of what a future Ubuntu will be, done with stuff that is not quite there yet.

---

### Post by upallnight on 2011-05-01
DO NOT DO NOT DO NOT UPGRADE!

I had a good working ubuntu setup and never had any problems when upgrading before Natty. After upgrading to Natty, Unity would give an error message saying my hardware does not support Unity and the keyboard/mouse wouldn't respond. Still can't use my computer! Natty sucks!

---

### Post by Dale61 on 2011-05-01
> **upallnight said:**
> do not do not do not upgrade!

I had a good working ubuntu setup and never had any problems when upgrading before natty. After upgrading to natty, unity would give an error message saying my hardware does not support unity and the keyboard/mouse wouldn't respond. Still can't use my computer! Natty sucks!

*Appropriate smilies don't even work now!*

---

### Post by Dutch70 on 2011-05-01
I NEVER do an upgrade. I tried it one time, it took forever, was over complicated, and failed miserably. 

Thankfully, I had/have a separate /home partition. So a fresh install was fast, simple & works great.

I also don't have problems with Natty, that are not expected from it being a new release. Compiz works fine in Ubuntu Classic. 

I'm guessing that most of the people complaining don't even know what/where Ubuntu Classic is. 
It's on the login screen, but doesn't show up until you put in your name & password.

Good luck

---

