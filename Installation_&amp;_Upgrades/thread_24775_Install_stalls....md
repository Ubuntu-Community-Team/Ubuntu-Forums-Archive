---
title: "Install stalls..."
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by RadixLecti on 2005-04-08
Hi,

When installing Hoary, it stops cold during the "Configuring apt...", "Setting up primary installation repository..." part. 25% completed, and then complete halt. I've tried waiting 10 minutes, I've tried installing again, but it hangs at the same place every time.

Could it be a bad cd? Or is there something else wrong? Warty installed like a treat.

---

### Post by kahping on 2005-04-08
i'm also experiencing stalls here. but mine is right after hoary detects my mouse :-(

that's with the Release Candidate, though, so i'll try again with the final release :-D

hope it works :-P otherwise, i'll be without Ubuntu for a while since i'm clean installing for this release.

kahping

---

### Post by bored2k on 2005-04-08
[QUOTE=RadixLecti]Hi,

When installing Hoary, it stops cold during the "Configuring apt...", "Setting up primary installation repository..." part. 25% completed, and then complete halt. I've tried waiting 10 minutes, I've tried installing again, but it hangs at the same place every time.

Could it be a bad cd? Or is there something else wrong? Warty installed like a treat.[/QUOTE]
 Never for forget to do and md5 check on your .iso's, specially distribution discs.

---

### Post by RadixLecti on 2005-04-08
[QUOTE=bored2k]Never for forget to do and md5 check on your .iso's, specially distribution discs.[/QUOTE]
 I downloaded a new .iso, checked the md5 and burned it. Same problem; it stalls at "Configuring apt...", at 25%, and won't go on.

Has anyone else tried the i386-iso and succeeded in installing Hoary?

---

### Post by RadixLecti on 2005-04-08
The problem seems language-related. I've been trying to install Hoary with Swedish as my language of preference... when I tried English, "Configuring apt..." worked like a charm.

Bug?

[EDIT] It worked once. Now it's haywire again. Also, it seems that under the English language, DHCP network setup works, and under Swedish, I get a static network setup... Wierd, huh?

I'm getting tired of this. I'm thinking of returning to Warty, the installer there WORKS.

---

### Post by RadixLecti on 2005-04-08
I've decided to try a few more times, but there doesn't seem to be much to do about it. 

I've tried switching to the console (alt-f4) to see whether something is happening below the surface, but the install seems completely frozen.

Could it be that the repositories are swamped? There ARE a few people installing Ubuntu now, I'd wager. ;)

---

### Post by Christoffer_V on 2005-04-09
I got exactly the same problem! When trying to install with Swedish lang I always get this error.
When I installed the RC of hoary it worked like a charm. Now it stalls at 25%.

Is their any fix for this? Or do I have to install with English?

---

### Post by HackeR_54 on 2005-04-09
same problem here, but I´ve tried Swedish / English non of them work!

EDIT: I GOT IT TO WORK LIKE A CHARM :P

When you get to the setup user press ESC and jump right away to install grub, lilo
when it reboots it will continue without the cd and setup user etc then it asks for cd just put it in and it said for me the cd isnt a valid one just use http then... it will work for a while and then its done!

---

### Post by alekzandr on 2005-04-09
[QUOTE=RadixLecti]Hi,

When installing Hoary, it stops cold during the "Configuring apt...", "Setting up primary installation repository..." part. 25% completed, and then complete halt. I've tried waiting 10 minutes, I've tried installing again, but it hangs at the same place every time.

Could it be a bad cd? Or is there something else wrong? Warty installed like a treat.[/QUOTE]
 Mine fails at the same "Configuring apt...", "Setting up primary installation repository..." part. 25% completed" stage. I have left it running all night, and it does not progress. There appears to be no way to skip this step, or exit once this happens. US English install. Does anyone know how to find out what is happening, is there a log visible on an alternate terminal?

---

### Post by madzzoni on 2005-04-09
[QUOTE=HackeR_54]same problem here, but I´ve tried Swedish / English non of them work!

EDIT: I GOT IT TO WORK LIKE A CHARM :P

When you get to the setup user press ESC and jump right away to install grub, lilo
when it reboots it will continue without the cd and setup user etc then it asks for cd just put it in and it said for me the cd isnt a valid one just use http then... it will work for a while and then its done![/QUOTE]

Did you set the username before or after the reboot?

---

### Post by HackeR_54 on 2005-04-09
After the reboot

---

### Post by ganesh on 2005-04-09
I also have the same problem with 5.04. In fact I am having this problem since Array 6 of Hoary. 

I found work around for this problem. 

Please refer to my following posts:

[1] [http://ubuntuforums.org/showthread.php?t=19408](http://ubuntuforums.org/showthread.php?t=19408)

[1] [http://ubuntuforums.org/showthread.php?t=18190](http://ubuntuforums.org/showthread.php?t=18190)

I do not know if it matters, but following is my hardware configuration:
I am using Dell Latitude C600 and I am installing from CD (This is at device /dev/hdc).

Let me know if this helps

- Ganesh

---

### Post by Topper on 2005-04-09
I experieced it too, but after waiting for ½ hour installation continued...not nice, but at least installation continued;)

---

### Post by benkorkor on 2005-04-23
anyone got solution to this?

---

### Post by crazybill on 2005-04-24
First, a former roommate of mine back when I was a student at Georgia Tech (Ulf Bergqvist) informed me on a revisit to this country that more people in the US speak Swedish than in Sweden! I found that interesting. It seems the population of Sweden and the population of the state of Georgia are about the same. Thus, there are as many folks in the US as in Sweden that probably want an answer to this.

But on to the computer problem. I had a computer that I could not install Hoary on. This is what I did: I installed Warty. which did work. Then I upgraded it to Hoary.

I modified the /etc/apt/sources.info  with **vi /etc/apt/sources.info** changing "warty" with "hoary" whereever I found it.. and saved the new file.
Then **sudo apt-get update**
Then **sudo apt-get dist-upgrade**
Then **sudo apt-get install ubuntu-base ubuntu-desktop**
I then edited** /etc/mkinitrd/mkinitrd.conf ** replacing the line 
**#RESUME= **
with 
**RESUME=/dev/hda5*****   (***note that hda5 was my swap partition, but your swap partition might be different. Check it out with **sudo fdisk -l ** or **tail /proc/swap** and replace **hda5** with the partition that is correct for your machine)
For Swedish language, you may find that it is necessary to install language-pack-xx, language-pack-xx-base and language-support-xx where "xx" should be replaced with the language code for the Swedish language.
Reboot.

I hope that helps you.

---

### Post by blakdogg on 2005-05-08
Ran into the 25% freeze while installing 5.0.4. Experienced the problem with both the i386 and am64 install CDs, same media, same burner and same pc. With amd64, I somehow managed to complete two installs out of 10-15.

Still struggling with i386

Tried the 'server' install workaround ...  but that froze while installing grub

Tried bailing on user config, and installing grub at that point ... downloading packages. Will followup

---

### Post by madzzoni on 2005-05-08
My problem with the "freezing-installer" was solved with, using a _SIMPLYMEPIS 3.3 Live-CD as root_, to get access to the /etc/network/interfaces in ubuntu 5.04 and edit the configuration to a STATIC setup instead of Aut. DHCP. 
Then i rebooted ubuntu and it connected to the internet and finished the installation with success :-)
For some strange reasons my ZITECH Barebone w/NVIDIA PC wouldn't accept DHCP in either debian Sarge or Ubuntu Hoary!

With Linspire, Simplymepis and Xandros 3.0 i got no problems with DHCP when installing.

---

### Post by LongTooth on 2005-05-08
I too have had this problem with Hoary. I've tried just about everything I could think of to solve it. But to no avail. You see, I could download ISOs of other distros (Mepis, DSL, PC-BSD, Knoppix), burn them and install them in my test box. To save money I've been using CDR-Ws. I've used the same CDR-W for Hoary that I used to burn the other ISOs. So it wasn't the medium. Same test box so that couldn't be the problem. All other installs work on my test box except Hoary. 

My install would stop at several places along the way. The error message was that some part of the program was in error and the suggested help was to burn my CD at a slower rate. Bittorrent, FTP, HTP, slower burn rate, nothing helped. I thought that once I got my pressed CDs the problem would be solved. I just got them yesterday. I rushed to my test box and...same problem. Well, hells-bells?! 

Of course I can install Hoary via the Warty, dist-upgrade method. But it is disapointing to see that this might be a bug in Hoary. Recently I had to reinstall Ubuntu/Hoary on my main box. Nothing wrong with the install but in a moment of pure, unmitigated dumbness, I screwed it up and thus a reinstall was called for. Still thinking I had defective CDs or bad burns I used my Warty CD to get Hoary back up and running. If I had know what I know now, I would have tried the downloaded Hoary burn on my main box to completely rule out a quirk on the test box. 

For a while I thought I was the only one having this kind of trouble. Now it seems that that is not so. I shudder to think of what this means. I've just received 20 CDs that I was going to pass out to friends and others interested in Ubuntu/Linux. Should I wait? I just might try a fresh install on my main box and see if I get the same results. But I'd hate to go through all that work. 

I'd be interested to hear from other and how and if they solved this problem. Thanks.

---

### Post by blakdogg on 2005-05-08
FOLLOWING UP .. IT WORKS :smile: 

As suggested earlier in the thread, I ESC'd out of configuring the user and went straight to installing GRUB. After the install the setup rebooted, and completed the install. - SO IT WORKED

Unfortunately, Setup claims that the CD was not valid after the reboot so I had to download all my packages off he net. I also have no sound, and i think my sond card was not configured.

---

### Post by LongTooth on 2005-05-08
OK, maybe you've found a work around. But for  newbies or even experienced user this is not the way to go when promoting a distro. The basic install should be as painless as possible without having to use a work around. I, or anyone else, might as well use the Debian net-install and work to get other programs installed to make our systerm preform as required instead of needing a work around on the initial installl! That's just insane! 

I believe this is a major glitch and it should be address as soon as possible before anymore pressed CD are send out. 

Am I the only one who has had this experience? I'd like to hear more from the Ubuntu community. Thanks.

---

### Post by poofyhairguy on 2005-05-09
I've had problems when I don't burn the ISO at low speeds. For some reason when I burn it at high speeds, it sometimes doesn't work. 

Try like 4x or 10x instead....

---

### Post by medication on 2005-05-10
[QUOTE=LongTooth]OK, maybe you've found a work around. But for  newbies or even experienced user this is not the way to go when promoting a distro. The basic install should be as painless as possible without having to use a work around. I, or anyone else, might as well use the Debian net-install and work to get other programs installed to make our systerm preform as required instead of needing a work around on the initial installl! That's just insane! 

I believe this is a major glitch and it should be address as soon as possible before anymore pressed CD are send out. 

Am I the only one who has had this experience? I'd like to hear more from the Ubuntu community. Thanks.[/QUOTE]
 I'm new to kubuntu and I loved the Live CD so i thought that I'd install it as my primary OS on a machine that I just built (AMD64)... unfortunately, I'm experiencing the stall at 25% trying to install.  I was able to install the base system using the 'Esc'->User Setup work-around but I was really looking forward to a better experience with the install.

I agree that this is should be addressed... I'm definitely willing to provide info to anyone if it would help.

---

### Post by alankstewart on 2005-06-11
It seems for me the problem is related to the CD I am using to install. I recently got a new NEC internal DVD DL burner/CD reader/burner for my Dell 8300, but all the Hoary ISOs burnt with this device do not get past the Configuring APT 25% mark. CDs burnt with my older burner never gave me a problem on the install.
Could be speed related on the burn as others have said. I'm going to try single speed to see if it works. If anyone's interested, I'll post the results.
Regards
Alan

---

### Post by woodraft on 2005-06-12
Hi all 

I'm having the exact same problem. My other PC is now just sitting there with 25 % progress. There is no activity from CD or harddisk. When I hop to console 2 and type ifconfig, I see my network is properly configured. I thought it might go on after a certain  amount of time, but now after .5 hour it is still not moving on.

I see that this topic started appx a month ago. Has nothing happened officially to fix or explain this issue since then?

I chose english language, Irish locale (EURO support) amsterdam timezone and us keyboard. This is actually my 5th try... still hanging in there. Could it have anything to do with my CD rom device? or my harddisk layout (that was just recently painfully fixed for use with windows after another linux distro nuked the partition table.... ;-( )Oh, by the way, Kubuntu installed fine a while ago on the same system.

---

### Post by alankstewart on 2005-06-13
I burnt a hoary install iso disk today at 2x speed and it installed OK
Regards
Alan

---

### Post by Bicky on 2005-06-16
Hello everybody,

I've kind of the same problem. During the instalation it just crashes and i can't do anything anymore, not even open my cd-player. 

I've tried another cd-player and another cd, other keyboard and mouse other graphic card.

Can you help me ?.

---

### Post by jsuen on 2005-06-16
[QUOTE=Bicky]Hello everybody,

I've kind of the same problem. During the instalation it just crashes and i can't do anything anymore, not even open my cd-player. 

I've tried another cd-player and another cd, other keyboard and mouse other graphic card.

Can you help me ?.[/QUOTE]
 sorry, what do you mean with 'just crashes' ? does it stall or just reboot again, or it gives you an error?
you can open your cd player after turning your comp off manually, other options i'd say is to burn the ISO again, maybe at a lower speed (i had problems too before with that). i don't think changing your keyboard/mouse/vga card would help entirely...

---

### Post by Bicky on 2005-06-16
it stalls, no error mesage or something. After I've put the reset button on my pc i can open my cd-player again (knew that, but it was just to say that it really doesn't works anymore).

I've ordered the CD's at this site, so that will not be the problem I think. But I will try it.

some more information of my PC:
AMD athlon thunderbird 1400mhz
128 mb SDRAM

can it have something to do with my bios ?

BTW: Same problem if I try to run te live-cd

EDIT: It works now, but when I start internetting it keeps stalling. I'd seen a topic about this but I wasn't able to find it anymore, can somebody help me out ?

---

### Post by Lord Kel on 2005-07-13
Hi There,

I am pretty much a noob when it comes to anything linux (I have successfully installed mandrake before but was never able to get my wifi card working)

I downloaded the iso today(13/07/05) and am experiancing the same problem with the instal (stalls at 25% configuring apt)

Now what I am trying to achieve is get an old laptop running with this (pent 300mhz, 64meg ram) and then get it on the net with a wifi card. Currently the laptop is not connected to the net and the only way it will be is via wifi, so I am at a loss as to why this error is occuring in the first place.

When it goes through the install it can't find any network devices (far enough as I have nothing attached).

I have rebooted several times and it still get stuck in the same place.

Is there any reliable work - arounds for this problem. I would really love to begin using ubunto but.. given the issues I'm not sure if its a good idea..


Edit: I have rebooted without the wireless card in and it now proceeds through the install o.k

---

### Post by MythBinder on 2005-07-18
Burning a New DVD at slowest Speed 2.4? according to Nero Fixed this Problem for me

---

### Post by dshadywun on 2005-07-18
[QUOTE=ganesh]I also have the same problem with 5.04. In fact I am having this problem since Array 6 of Hoary. 

I found work around for this problem. 

Please refer to my following posts:

[1] [http://ubuntuforums.org/showthread.php?t=19408](http://ubuntuforums.org/showthread.php?t=19408)

[1] [http://ubuntuforums.org/showthread.php?t=18190](http://ubuntuforums.org/showthread.php?t=18190)

I do not know if it matters, but following is my hardware configuration:
I am using Dell Latitude C600 and I am installing from CD (This is at device /dev/hdc).

Let me know if this helps

- Ganesh[/QUOTE]
 MAKE EASY MONEY ONLINE WITH PAYPAL!

PLEASE READ YOU WILL BE THANKING ME LATER   :)

Have you ever wanted to make some money online. I have not had much success up to this point. To be honest I am totally sceptical about any get-rich quick scheme I have ever heard about.

Well then I found this PayPal Money making guide. I read some more about it and saw people reporting that they had made a few thousands of dollars. Well of course I didn’t believe it. Would you.

Then I decided to try it. So I looked for a mailing list and sent 5 dollars to every person on that list then entered my name. It only cost me $25, which is cheap compared to what i made from it!!!

Now its time for the next stage,  posting my message on numerous message boards. The reason for posting messages is so u can get more people to send!

And the more people who send the more money you make and the more money they will eventually be making.

Hopefully there are enough people out there who will see this message and take the chance, so that this will work and make alot of people alot of money.

If you past this up now and relize later that this really works, you will regret not trying it sooner? If you start now just imagine all the money you will make in a few months it will definitly be in the thousands.

Ive been doing this for 3 months and already have $5,540. And theres still money coming in!! Im just trying to spread the word so that everyone can enjoy this as much as i am.

So here’s the 5 step plan.

1. Copy this letter and save it in your computer and/or on a floppy disk. I suggest you print this for future refrence. :)

2. Send 5 dollars to every PayPal account on the list below (If you don’t have PayPal sign up for one at this link: [https://www.paypal.com](https://www.paypal.com))

1) [email]krstic12@hotmail.com[/email]
2) [email]gatman973@yahoo.com[/email]
3) [email]nets45@walla.com[/email]
4) [email]tedd745@yahoo.com[/email]
5) [email]dshadywun1@yahoo.com[/email]

IMPORTANT: when u send the money please include the comments "Please add me on your mailing list" this makes this whole process legal.

Question:  Why send people money?         Answer: IF you dont send money to the e-mail addreses your chances of making money off this are slim. The reason for that is, When you send money and ask them to "Please add me on your mailing list" they will put your e-mail on there ads. Therefore your e-mail  will spread dramaticly over thousands of forums for people to see so will make you alot of $$$$$ MONEY $$$$$!!!!

 The next step is important so pay attention!

3. After sending the money to the paypal accounts, What you need to do is....

Remove the e-mail from the number 1 spot off the list. ( THIS PERSON IS NOW OFF THE LIST BUT IS NO DOUBT COUNTING ALL HIS MONEY!!!)
Then put the e-mail from the number 2 spot in the number one spot.
Then take the e-mail from the number 3 spot in the number 2 spot.
Then take the e-mail from the number 4 spot to the number 3 spot.
Then take the e-mail from the number 5 spot to the number 4 spot.

Ok now there is the last empty spot put your e-mail in this spot. So when your done it should look like the list below.

1) [email]gatman973@yahoo.com[/email]
2) [email]nets45@walla.com[/email]
3) [email]tedd745@yahoo.com[/email]
4) [email]dshadywun1@yahoo.com[/email]
5) YOUR E-MAIL

4. You could use this letter to send to your friends and post on forums. Try to post this on all the sites you possibly can because people who see this. The more money you will make.

5. Sit back and just watch your paypay account get filled with money. Dont spend it all at once!!!!!                     

Thank you

---

### Post by floppy on 2005-08-06
[QUOTE=blakdogg]FOLLOWING UP .. IT WORKS :smile: 

As suggested earlier in the thread, I ESC'd out of configuring the user and went straight to installing GRUB. After the install the setup rebooted, and completed the install. - SO IT WORKED

Unfortunately, Setup claims that the CD was not valid after the reboot so I had to download all my packages off he net. I also have no sound, and i think my sond card was not configured.[/QUOTE]

This method also worked for me, completely without problems. Everything, including sound, is working fine. After the reboot I had to install packages from the net, also, but that wasn't a big deal.

I tried numerous methods prior to this, none worked. It seems to be a problem with configuring atp during the intial install process and appears to be network setup related.

---

### Post by jaime_vives on 2005-08-20
Hi All:

  Good news... perhaps your problem is similar to mine and you can use my experience at solving it:

  This morning I was trying Ubuntu for first time, and encountered the exact same problem (hang at 25% of the primary repository setup). After retrying several times with typical boot parameters, I found that the problem was my SCSI card for the HP Scanjet 5P. It is a sym53c416, and I saw a tip for a similar card on the installer help, so I used this when booting:

  linux sym53c416=safe:y

  It worked nice and now I'm finishing the installation after a successful reboot... :)

  Hope this helps!

--
Jaime

---

### Post by UNHOLYwoo on 2006-01-19
I am having the same problem (why else would I be posting here esp as my first post)... anyways, heres something I can add to the confusion:

I have an official live/install cd set, both 5.04 and it does this. The odd part is that I've isntalled off this disk before, about a week ago... and it has been in the case ever since.

---

### Post by PBK on 2006-03-16
I had the same thing happening here. My problem was my NEC ND 3500 DVD drive...
  
  I just downloaded Ubuntu 5.10 last week to try it out. Loaded it on a few computers with no problems. Distro looks great (Thank you!) so I ordered a new hard drive and DVD drive to upgrade a system for my MythTV box. The hard drive is a WD 320Gb SATA, BTW.

  Now, with new drives, I attempt to load Ubuntu. All looks well until I get to the  part about configuring apt... 25%. Locked. After reading something in an earlier post, here, I remembered that I built a Windows XP computer a few weeks back and had similar problems. I see from my records that it's the same DVD drive! Stupid me; 1st time shame on you, second time shame on me. That first time I placed a call to NEC and they mentioned that the firmware needs to be upgraded in order to install new from the DVD drive. 

  I temporarily replaced the DVD with an old CD drive and all loaded without problems. After installation, the DVD drive works fine.

  I just wanted to hopefully let someone else know of a possible solution and to thank all the Ubuntu team for a very promising Unix/Linux distribution. I have to learn it better and might plan to push it on the streets around my neck of the woods!

Paul

---

### Post by arthur on 2006-03-18
Well, I am (sort of) glad I am not alone. Same problem here.
The funny thing in my case: I already installed 5.10 before, using exactly the same HW, and it did not freeze. Why should it do this only "sometimes"?

Weird. Will try the workaround (not setting user).
No solution for this yet? :confused:

---

### Post by arthur on 2006-03-18
Started installation again (4th attempt):
SETTING APT STALLS, even not defining the user :mad:

---

### Post by arthur on 2006-03-18
Fixed it:
[B]
DOWNLOAD LOCAL LANGUAGE SUPPORT? 
SAY NO
SET UP USERS? 
PRESS ESC[/B]

That will do the trick :-D

---

### Post by abqGold on 2006-04-27
OK, got around the apt@25% hang using a mixuture of advice from above:

Chose British, rather than American (does screw up the KB a bit ;)  )
Chose ext3 rather than LVM partition
Escaped out at set up users, and continued with install from install grub
On reboot, removed CD, and waited for installer to ask for it again

Unlike other posts, at that point the CD was used succesfully to complete the install.

I really have no idea which steps made a difference, and which didn't; only that I have a very nice ubuntu installation now, and did not have to http stuff to complete the install.

---

