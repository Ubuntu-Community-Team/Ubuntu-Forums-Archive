---
title: "[SOLVED] How to do a clean install with encrypted file system and keep my NTFS partit"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-03-16
I'm installing Kubuntu on a HDD that has two NTFS partitions I need to keep. I'm using the alternate CD (partly because the live CD won't work on this computer).

I want to install Ubuntu with everything (except /boot) encrypted, including the swap partition.

I have a 150GB raptor with these partitions:
1. primary 31.5GB boot NTFS
2. free space 34.4 GB
3. primary 80.0GB NTFS
4. free space 4.2 GB

I'd like to use that last free space for the swap file. I have 4GB of RAM, so it is about the right size.
I'd like to put Ubuntu in the 34.4 GB free area. I can use all the free space for Ubuntu.

Since I can't use the Guided Partitioning, how should I go about setting this up? Thanks.

---

### Post by MountainX on 2008-03-17
I do not have this resolved yet, but I found two good links:
[http://ubuntuforums.org/showthread.php?t=582406](http://ubuntuforums.org/showthread.php?t=582406)
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

I'm continuing to work on it. Right now I'm getting the error "Failed to remove conflicting files" "The installer needs to remove operating system files from the install target, but was unable to do so."

I haven't solved that error yet...

UPDATE:
This error is apparently a known bug in Hardy alpha. Some messages indicated it had been fixed after alpha 4, but I'm using alpha 6 and the issue is still there.

---

### Post by MountainX on 2008-03-18
This is an issue related to Hardy alpha. I have done what I wanted about 3 - 4 times now with Gutsy, but I can't do it with Hardy (either alpha 6 or current daily build). I'm giving up and marking this thread as solved. The solution is to simply not try this with the alpha build of Hardy yet.

---

### Post by newbieforever on 2008-03-29
hello,
i'm interested in making a clean encrypted linux installation;

i have many issues about ubuntu (please see [http://ubuntuforums.org/showthread.php?t=736901](http://ubuntuforums.org/showthread.php?t=736901))

may be mepis is better from some point of view: no compromise with the possibility to have a "hardcore" deb-based linux, but much easier installation, support and management

i continue to choose ubuntu only to have the chance to be hooked to the distro that will surely be the most widely used in many environments in the early future

i strongly disagree the arbitrary "one-way-only" ubuntu repos policy (see the wll known getdeb.net --> about)

having about 300,000 files installed as gutsy, yesterday i performed the the hardy rc upgrade: i got hundreds of errors, and i dont feel like the final release of hardy will fix all those problems in a snap

back to subject matter: could you help me?
do you think is it good perform this morning an encrypted installation with the 7.10 alternate cd, spending time to 
setting all the system one more time, then upgrade to hardy in a month and afford the risk to have a mountain of legacy versions of the software i need, and in addition having troubles with the encrypted fs management?

thank you very much

nbfe

---

### Post by MountainX on 2008-03-29
I recently did a clean install of Hardy beta with a fully encrypted file system and it is working well. I too have some new problems in Hardy that were not present in Gutsy. But if people like you and me don't use Hardy beta and don't report these bugs, then surely they will not be as likely to get fixed. If you are going to do a clean install, why don't you go ahead and install Hardy. The encrypted file system part will work. I can offer more specific advice if needed.

---

### Post by newbieforever on 2008-03-30
> **MountainX said:**
> I recently did a clean install of Hardy beta with a fully encrypted file system and it is working well. I too have some new problems in Hardy that were not present in Gutsy. But if people like you and me don't use Hardy beta and don't report these bugs, then surely they will not be as likely to get fixed. If you are going to do a clean install, why don't you go ahead and install Hardy. The encrypted file system part will work. I can offer more specific advice if needed.

hello MountainX, thank for your kind reply...
1 - i definitively agree with you and what you said;
2 - i did install gutsy with "complete" encryption: unfortunately my notebook cant afford the loss of performance...
3 - so i thought to encrypt only the /home partition.. even this resulted in very heavy duty for my processor... my fan went crazy...
i was obliged to turn back a normal installation
4 - i also seen that in italy filesystem encryption is bad seen by authorities... i think there are other means to protect myself... not so "striking"... :-)

5 - apart hardy heron problems, which i will afford anyway, there's a point:

i would be glad to test new features, but where i have to submit bugs and feature proposals? where could speak to get my voice listened? there are millions of complains and suggestions in the ubuntu forums, and nothing of those is ever listened... the guide and the wiki never include solutions to thousand of recursive problems and desires

if i cant submit my problems to people who really count in ubuntu development, where is the sense?
am i missing something? is there an ubuntu bugzilla and "desiderata" public places?
please forgive me, im on ubuntu from some weeks... may be i lost something...

nbfe

---

### Post by MountainX on 2008-03-30
> **newbieforever said:**
> 
i would be glad to test new features, but where i have to submit bugs and feature proposals? where could speak to get my voice listened? there are millions of complains and suggestions in the ubuntu forums, and nothing of those is ever listened... the guide and the wiki never include solutions to thousand of recursive problems and desires

if i cant submit my problems to people who really count in ubuntu development, where is the sense?
am i missing something? is there an ubuntu bugzilla and "desiderata" public places?
please forgive me, im on ubuntu from some weeks... may be i lost something...

nbfe

You raise some good points. I'm also concerned about the same thing. In particular, there is [this gedit/cifs bug]("http://ubuntuforums.org/showthread.php?t=738168") that hasn't been fixed for over 2 years and who knows if the messages are getting through to the right developers?

Here is something I'm looking into myself that might be win-win:
[https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day)
Notice it says, "If you want to just confirm new bugs, you can do that."
Also notice that there are** automated bug reporting tools** and other helpful tools that are part of that program.

See this blog post for more info:
[http://bobbocanfly.wordpress.com/2008/02/22/ubuntu-5-a-day/](http://bobbocanfly.wordpress.com/2008/02/22/ubuntu-5-a-day/)

I don't know much about the program yet, but it looks like it could be a great way to address the concerns you expressed while also helping the entire Ubuntu community.

---

### Post by newbieforever on 2008-04-02
thank you very much mountainx, i really appreciated your comprehension and suggestions about bugs and features proposal submission!
that's the most valuable info that you gave to me...

i appreciated also the info about encryption, but im at the following point:

--> i will let you know about my progresses asap, likely when i will have time to upgrade to hardy...
my first problem about hardy with firefox 3, is that i strongly need firefox 2, because aside eclipse, tomcat, and mysql is the most important app to me... and i'm hooked to firefox extensions, not to firefox itself... firefox 3 doesnt support (or viceversa) the key extensions i use... 
in the meantime i satisfy my privacy/safety/security-related needs with truecrypt... i noticed that it is significantly faster and richer in features than the built in partition encryption shipped with ubuntu, and i can control it with fine grain settings... in the end, i took information about the subject, and i found that professional encrypted partition or system are very bad seen by italian authorities...
you know... in italy an incredible % of professionals and society make an indiscriminated  use of somehow "cracked" or "not licensed" software, and if you encrypt your disk they instantly assume that you also are doing that, while i paid every single bit of proprietary code i used since from my first computer!!!!!

thanks again, c u soon, 

sincerely, nbfe

---

### Post by MountainX on 2008-04-02
newbieforever - I appreciate your reply. I understand what you mean about Firefox. I am having some difficulties living without certain extensions while I am using FF3. It is probably possible to install FF2 in Hardy, but so far I have not wanted to try. I'm going to try to get by for the next month or so without my extensions.

I also agree with you that TrueCrypt is excellent.

---

### Post by newbieforever on 2008-04-03
> **MountainX said:**
> You raise some good points. I'm also concerned about the same thing. In particular, there is [this gedit/cifs bug]("http://ubuntuforums.org/showthread.php?t=738168") that hasn't been fixed for over 2 years and who knows if the messages are getting through to the right developers?

Here is something I'm looking into myself that might be win-win:
[https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day)
Notice it says, "If you want to just confirm new bugs, you can do that."
Also notice that there are** automated bug reporting tools** and other helpful tools that are part of that program.

See this blog post for more info:
[http://bobbocanfly.wordpress.com/2008/02/22/ubuntu-5-a-day/](http://bobbocanfly.wordpress.com/2008/02/22/ubuntu-5-a-day/)

I don't know much about the program yet, but it looks like it could be a great way to address the concerns you expressed while also helping the entire Ubuntu community.

hello mountainx,
excuse for the delay in replying...
i'm pleased to talk to you...
thanks for understanding me, your post is clear, and gives me important information, as i said...
i only wanted to mention for you a link that could seem something similar to bugzilla...
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
please forgive if i'm quick and dirty... :-) i'm in a hurry...
anyway i hope this could be a little help...
if you please, let me know what you think about it...
actually i didn't use it yet...

good bye,

nbfe

---

### Post by newbieforever on 2008-04-03
> **MountainX said:**
> newbieforever - I appreciate your reply. I understand what you mean about Firefox. I am having some difficulties living without certain extensions while I am using FF3. It is probably possible to install FF2 in Hardy, but so far I have not wanted to try. I'm going to try to get by for the next month or so without my extensions.

I also agree with you that TrueCrypt is excellent.

ps: about FF2 and 3 living together  i can say that i upgraded to HH beta yesterday, as you can in another thread i started, and beside a lot of problems due to a dummy debian repo i added following the advice of one forumist... i can see 2 and 3 on the same system, without any interference... the only relation is that 3 ask you if you want to import 2's configuration or to start from scratch... 

and staying in the focus of this thread i wanted to say to you that just when HH final will be released on alternate CD i will use the encrypted file system... plus truecrypt... who will want to see my stuff will have some additional work to do... :-)

cu soon

nbfe

---

### Post by MountainX on 2008-04-03
> **newbieforever said:**
> ps: about FF2 and 3 living together  i can say that i upgraded to HH beta yesterday, as you can in another thread i started, and beside a lot of problems due to a dummy debian repo i added following the advice of one forumist... i can see 2 and 3 on the same system, without any interference... the only relation is that 3 ask you if you want to import 2's configuration or to start from scratch... 

and staying in the focus of this thread i wanted to say to you that just when HH final will be released on alternate CD i will use the encrypted file system... plus truecrypt... who will want to see my stuff will have some additional work to do... :-)

cu soon

nbfe

Excellent report. Thanks for the info. :)

---

### Post by newbieforever on 2008-04-04
> **MountainX said:**
> You raise some good points. I'm also concerned about the same thing. (..)
please don't consider me _only_ a boring dummy, but if you please, you could see this post of mine... thank you...
[http://ubuntuforums.org/showthread.php?p=4645479#post4645479](http://ubuntuforums.org/showthread.php?p=4645479#post4645479)
if only mepis or dreamlinux had a better hardware support, i would turn to them...
even if i really love ubuntu... but ubuntu (i read an entire italian book on it, and his story) is not as "community (only) based" as we are used to think...
--edit---
[http://ubuntuforums.org/showthread.php?p=4651413#post4651413](http://ubuntuforums.org/showthread.php?p=4651413#post4651413)
[http://ubuntuforums.org/showthread.php?p=4649681#post4649681](http://ubuntuforums.org/showthread.php?p=4649681#post4649681)

---

