---
title: "Issues intalling Linix distro on 2 computers 4 different distros tried on one of them"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-03-21
I appologize if this has already been posted but there are 1001 pages here and I did do some searching - I'm just soooo tired by this point. This whole linux thing is starting to lose it's luster.
 
If anyone can please please help.
 
I've never used linux before and wouldn't know how do deal wtih command line anything - whether its understanding what the system generates or entering it.
 
For the last 3 days I've tried to install, first - xubuntu, then openSuSe, then ubuntu desktop on my desktop unit then to run ubuntu netbook live on my laptop with the intent of doing a permanent install (if I could see I would be able to get everything working right by trying live first).
 
So I follow the instructons given on the ubuntu site, using the universal usb creator - it tells me that the operation was successful or something like that. So I proceed to 'attempt to' boot from usb but I find out my bios (on the laptop) does not support booting from usb (go figure!). So I go get this thing called PLoP, burn the .iso to a cd, put the cd in my drive and the usb inserted in the computer too and I reboot and enter my boot menu, select to boot from the optical device (my cd with PLoP on it) and use PLoP to select and boot from usb. Ubuntu runs for a bit I get past the logo with the status bar under it, then I get all this techo whatchamo spit out at me on the screen. Don't know what it means, just know it means I won't be enjoyin any Ubuntu tonight. Very sad.
 
I did manage to type in help and hit enter and in the list of commands given I noticed one that I though was interesting. "exit" So I put in exit and hit enter and it spit out a bunch more stuff at me. I only mention this because that is what is in the pictures I've attached. One pictures is before entering "exit" (on the laptop) and the othe after entering "exit" (on the laptop). There is also one that shows the screen from my desktop (after entering "exit"). I tried to run Ubuntu live one last time on it right after my last laptop fiasco; and, if you notice, some of the same information is given between the desktop and laptop. (matching infromation between the machines is after entering "exit" on both machines).
 
I attached the pictures and specs on my laptop hoping they may be useful.
 
I've done all I know how and I'm just starting to get really tired here. If I wasn't so sick of Windows I'd have probably given up by now. I just can't bring myself to blame Ubuntu though. I am certain that Ubuntu is fine. Its either, first, user error, or somthing with my machine. Just that Ubuntu says the same thing about both machines. Hope someon can help. Sorry for the long post.
 
Jake
:confused:

---

### Post by ClientAlive on 2011-03-21
Please someone help. I know I don't know much about working with this stuff but I would really like to try Ubuntu out and haven't been able to get anything to work (not even trying it out live). I'm absolutely stuck. There is nothing I know to do from this point and I have nowhere to turn for help but here. I'm just sitting here not able to move forward or do anything.

---

### Post by uRock on 2011-03-21
Please wait 24 hours before bumping your thread.

Someone with the proper talents may not have had a chance to see your thread. That said, please be patient.

Thanks,
uRock

---

### Post by tordeu on 2011-03-21
If you have a CD drive in your computer, then it seems really weird to boot from a cd to get Ubuntu booting the usb drive.

Why don't you burn the iso-image on a CD and boot Ubuntu directly from the CD?

---

### Post by jtzero on 2011-03-21
Im with tordeu on this one it looks like the cd is trying to boot, not install...
burn this to a cd
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

boot from the cd and follow the gui instructions

in fact it appears that the computer is trying to boot from the usb in the third attachment and failing, so make sure when you use the cd the usb is unplugged

btw Ive never used PLoP.... never needed to

---

### Post by walt.smith1960 on 2011-03-21
My success with creating and booting USB drives has been mixed, some machines will and some machines won't.  I've found live (bootable)  CDs slower to load but more reliable.  Just download a desktop .iso and use a CD burning program to create a bootable live CD.  I would recommend an i386 desktop release.

---

### Post by ClientAlive on 2011-03-21
Thank you sooo much everyone for your reply.
 
I want to clarify something first if that's ok.
 
I do want to do an actual install on my laptop but _not_ before I run it live and see that I can at least connect to the internet and all the other basics are functioning properly. I had been reading that this (internet thing) is sometimes an issue for people and I can't afford to have both my machines down and no way to connect to the internet.
 
----------------
 
* Tordeo, you say:
 
"If you have a CD drive in your computer, then it seems really weird to boot from a cd to get Ubuntu booting the usb drive.

Why don't you burn the iso-image on a CD and boot Ubuntu directly from the CD?"
 
The thing is, the option to boot from USB is not available in my boot menu. This link [http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/) shows a picture of exacly what my boot menu looks like. The information on that page is what I went by to get my machine to boot from USB. It tells you about PLoP and that's what I did.
 
There is also a lot to this story that hasn't been told in my original post (it's just too much to tell).
 
Specifically though, I did buRN the image (before going the USB route), well, to DVD anyway, and I still have that DVD sitting here. When I tried to run it live that way I ran into a dead end also - just a different dead end. See attachment named: "UbuntuNetbook_From_dvd" What is shown in the (new) picture is about where everything comes to a halt. That pop up box fades away after a about 30 second then the machine just sits there with nothing but that background and does nothing more. On one occasion I let it sit for 15 minutes (I timed it) and nothing more happened.
 
* jtzero, you say:
 
"in fact it appears that the computer is trying to boot from the usb in the third attachment and failing, so make sure when you use the cd the usb is unplugged"
 
My attempt to run this live from DVD and then from USB was separated by several hours; and, at the time I tried from DVD, the usb was not in the machine. The time I tried from USB what was in the disc drive was PLoP or else I wouldn't even be able to boot from USB at all. I had to use some kind of boot manager (PLoP in this case) or I wouldn't be able to boot from USB - so it would have been impossible for this machine to be trying to boot from USB  at the same time as the DVD - I think.
 
I'm really stuck on this one guys. I'll try running from DVD again right now but I did that so many times yesterday with the same result that I don't have much hope anything will be any different this time.
 
Also, the Ubuntu website tells you in step two: "Why do I need a USB drive?Using a USB stick means that you can trial Ubuntu without affecting your current system. And you can install it alongside or instead of your system whenever you're ready." This can be seen here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
 
----------------
 
I was reading the output from Ubuntu though and I got to wondering about a couple things it is saying (this can be seen in the picture attached on my original post).

 
It says stuff about: " . . . line 65: can't create/root/etc . . ."
 
and stuff like: " . . . nonexistent directory"
 
and on another line: "Setting up console keyboard . . . no such file or directory . . ."
 
This thing about "no such file or directory" and "noexistent directory" all throughout this list of information.
 
In the eight line down from the top of the screen in this picture it tals about and "invalid argument" (programming stuff)
 
Near the very end it seems to make a suggestion when it says: "no init found. Try passing init= bootarg"
 
These are just my observations but I don't really understand what it is saying.
 
Ultimately though I have tried both from DVD and USB and ran into problems with both and on both machines.
 
I wonder if there is a difference between CD or DVD though. Or maybe my USB is either bad or not compatible with this type of endeavor (making a bootable drive out of it).
 
Any more ideas?
 
Thanks . . .

---

### Post by ClientAlive on 2011-03-21
Thanks Walt. I'm gonna try again from DVD; and, I guess, I can burn a CD (as opposed to DVD). Don't see how that would make any difference though.

---

### Post by walt.smith1960 on 2011-03-21
> **ClientAlive said:**
> Thanks Walt. I'm gonna try again from DVD; and, I guess, I can burn a CD (as opposed to DVD). Don't see how that would make any difference though.

I don't know that it would matter if your DVD drive is of fairly recent vintage.  Older DVD ROM drives did have problems with reading DVD-Rs. Linux Mint which has a larger .iso (it includes more stuff) requires a DVD.  You're wise to see what works and what doesn't, especially wireless networking.  Ethernet connections are pretty much plug & play.  Wireless, especially recent and/or 802.11N chipsets can be easy or it can be a real pain.  If wireless turns out to be a problem, I'd recommend checking again when Natty 11.04 is released.  That kernel seems to have built-in support for many recently released chipsets.

---

### Post by jtzero on 2011-03-21
the netbook version assumes you dont have a cd/dvd drive as  a lot of (most?)  netbooks dont have it so they can be more compact. as a side note you  can run the (at least the desktop version) live without effecting the existing system on dvd, what version are you running with the dvd? (im assuming the netbook version, I wouldnt see that installing the netbook version from a cd would be a problem, but you never know.)

if the gui does come up at any point and the computer freezes press Ctrl + Alt + (one of F1 thru F7) one will show an error log (I think F1), F7 should just return you to the gui

---

### Post by tordeu on 2011-03-21
I also would recommend to burn the iso to a ordinary CD and try to boot from there. If the same problem with the pop-up box and nothing else happening does rise again, we can try something different. 15 Minutes is too long, but actually booting the live CD is pretty slow.

Do you mean that there really is just a background image and not a panel on top/bottom or something else?

---

### Post by ClientAlive on 2011-03-21
THanks guys.
 
jezero I was trying to run netbook 10.10. Can't recall if I've tried running the desktop version on this machine. I did download this netbook 10.10 iso from torrent but got the link through ubuntu's site so didn't see how it could hurt (its a lot faster download). Right now I'm downloading the iso in the normal manner from ubuntu's site (will take nearly 2 hrs is what I'm getting). my cd/dvd drive is fairly modern - I think (this computer is about 5 yrs old).
 
Lately I've gotten to wondering if I could start with an older version and climb through the updates to get to netbook 10.10. This seems kind of counter-intuitive and would be a lot of work for something that may, in the end, be a kind of patched together os. I don't know.
 
Gonna try burning the iso I get through a straight forward download (not torrent) from the ubuntu site and burn that on a cd (not dvd).
 
I think I feel kinda sick over this whole thing - think I just threw up in my moiuth a little bit - lol.
 
Thanks guys.
 
Jake
 
PS: After my post just previous to this one - I tried from the dvd again (netbook 10.10 that is - same one I've been after all along on this machine). The result? Same as before only, this time, I went out for an errand and let the thing sit for what amounted to 1hr 13 min (I timed it). When I got back it was still on the screen with nothing but the background in it. Hadn't moved the whole time. So now I'd say its beyond a shaddow of a doubt conclusive. It's not working from that dvd.

---

### Post by ClientAlive on 2011-03-21
Still stuck in the same situation.
 
Tordeu: I did burn the iso to a reg. cd and its the same situation. Gets to that pop up then the pop up dissapears then nothing. The iso I used for this cd is the one you get from a straight forward download (not a torrent) from the ubuntu web site too. So I know it's right.
 
jtzero mentioned hitting ctrl + alt + F1 I think to get the error message assosiated with this. As soon as I post this I will reboot that cd and try this. If I get the error read out I'll take a picture and come back and attach it.
 
Oh, just in case it helps: I used CD Burner XP to burn the image. It gives some relatively detailed info about the burn as it's doing it and seemed to do the job successfully. I burned it at 4x (the slowest setting).
 
Thanks
 
Jake
 
-------------------------
 
Just attached 2 pictures of the screen I get after hitting ctrl+alt+F1
 
The picture " . . . 001" is exactly what comes up. Picture " . . . 002" shows the results of me typing a couple things in from the help menu I brought up to see if I could get it to tell me more. Not really sure what I'm looking at (or what I'm doing) but it didn't seem like I got what I was hoping for. I was hoping to get an error message/ readout that explained what is going on when it stops loading up live like that.

---

### Post by supershin on 2011-03-21
Is your laptop compatible with that version of ubuntu? It could be that there are certain bugs or issues which could be the cause of your problem.

Check this link for your model - [https://wiki.ubuntu.com/LaptopTestingTeam/FAQ]("https://wiki.ubuntu.com/LaptopTestingTeam/FAQ")

If its not there search round for the laptop model compatibility/testing issues page. It may have a solution for you there.

---

### Post by ClientAlive on 2011-03-21
supershin: thanks for the link. I didn't see my exact model there per se - but I did see other pavilions there. I think the dv was something that was a more expensive/ better computer and that it was around when I bought this one (not sure I'm remembering correctly though). My computer is an HP Pavilion ze2000 but I opted for a couple changes from the base model. Its been about 5 years and what I can remember is I went with more ram than the base package but less hard drive than the base package. I think that was the only differences.
 
I wonder if any of the pavilions listed are close enough to mine that the information on one of them may be useful?
 
Hmmm . . .
 
---------------------------
 
Just looked through all six HP Pavilion entries in the link supershin gave me - wondered If I might find some useful info (even though none of them are my computer exactly). I'm not sure any of those systems are as old as this one though. The link to the manufacturers website sometimes brings up a machine that is currently being sold and sometimes not.
 
About half the reports address the issue of whether ubuntu installs on the machine and the ones that do address that all say "yes" that it does.
 
As I skimmed throught the rest of the info in these reports - the one thing I think I'm discovering is that it really isn't linux that the bug issues stem from as much, its the sloppy work of manufacturers who know they can get away with that kind of crap with a window os. * Please correct me if I'm wrong.
 
I think what I need is Super Duper Uber Geek to come to my rescue - redirect a sattelite and position it over the top of my appartment, take remote control of this stinkin' laptop and just make it all better. LOL!!
 
:)
 
------------------------------------
 
Take a look at this guys [http://ubuntuforums.org/showthread.php?t=1559695](http://ubuntuforums.org/showthread.php?t=1559695)
 
do you think what they are talking about could help me? I'm concerned that they are talking about 'installin' not running it live. Like I mentioned before, I do want to install but not before running ubuntu live first and being sure I have internet at least.
 
Let me know what you think.

---

### Post by tordeu on 2011-03-22
I just saw that your model has a 855GM Intel chipset. The 855GM is pretty old and there are some problems with it, so I assume that this is indeed where the problem with your laptop lies.

Here are two interesting Links about the 855GM problems:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)
[http://ubuntuforums.org/showthread.php?t=1612661](http://ubuntuforums.org/showthread.php?t=1612661) (see Post #7)

---

### Post by ClientAlive on 2011-03-22
tordeu:
 
Thanks for the links. Please forgive my writing such long posts and asking about so much. I do want to _just fix the problem_ and I also want to understand more too. As much as you are willing is fantastic in my eyes. All your effort is very much appreciated.
 
So there has been something bugging me this whole time now.
 
'Isn't there some way to get ubuntu to just tell what the problem is directly and specifically right from my machine?' I mean, maybe it wouldn't be in plain english per se but to get it to just list exactly what is going on and at what stage it's going on?
 
Also, can that solution (mentioned in your second link and described in your first one) be done for running ubuntu live? I'm just afraid to do a real install before trying this out live. If the install were to not work I'd be **** up a crick'! Well, of course, I could re-install windows - but all this wouldn't be much fun to go through?
 
You know, reading what was at that first link you gave me (and a link within that page) made me wonder about a lot of things. I thought about including them here and I even wrote it all out but I wasn't sure it would be right.
 
Thanks
Jake
:)
 
------------
 
What I was really getting at about making ubuntu tell you what's going on - is that this would be a method of diagnosing a problem that is very certain. If that is possible and if I could learn it, it would really be something huge for me. I guess there really is no way to say that without the possiblity of sounding rude but I really don't intend it that way.
 
Thanks

---

### Post by tordeu on 2011-03-22
Don't worry, this is the right place for asking questions.

The thing is that I can't be absolutely sure that the 855GM is in fact the problem. But giving that your laptop has this chipset and that there are others with similar problems for at least Ubuntu 10.04 and 10.10, I think that this is likely the cause.

Also, I forgot to mention that I have indeed a laptop with a 855GM lying around here. I had problems with 10.10 as well. I just did not think of it before, but when you posted your model and I saw that 855GM and after my last post, I just remembered that I was trying to install Ubuntu 10.10 on this thing (an Acer, but 855GM as well). I had this problem on 2 laptops in fact, although I don't know which kind of chipset the other one has.

I can't tell you how to figure out if it is in fact the chipset and I do not know when this problem started (which Ubuntu version). BUT: What I can tell you is that I could in fact install the test version of the new Ubuntu 11.04, which will come out on April 28th(?) on the laptop with the 855GM chipset.
You an already download test versions [here]("http://cdimage.ubuntu.com/daily-live/current/"), but the problem is that the download currently often have size issues and are too big for regular CDs. But you could try to download the test version of Natty (the i386 .iso) and burn it on a DVD/DVD-R and try if this works for you as well.

I do have some small graphics issues with Natty on the 855GM and I have not tried a specific Intel driver, but it does in work. I don't remember if I tried the live system, but I assume that if the fresh install works, the live system should work as well. I think this might be worth a try and as 11.04 is just around the corner, I think this would be the best way of "fixing" the problem.

As far as understanding problems like this goes: It is not always easy to figure out what really causes a problem and why and I can't help you with understanding this issue as this is too specific and seems to only be a problem for specific Intel chipsets. I do think it is great, however, that you want to understand the problem as well. Unfortunately I can't tell you there, as this would be a question for someone who has real experience with this 855GM issue or knows more about this stuff in general.

So, ultimately, I think there are three options:

1. Trying the fix for 10.10, which might require an install first (cause I am not sure about using that fix on a live system as well)
2. Use an older Ubuntu version which does not have the problem
3. Try Natty

I understand that you don't want to install first and then try to fix the problem afterwards. And I would not - in general - recommend an older Version of Ubuntu, cause you will miss out on a lot of stuff. Therefore, as I mentioned before, I would advise you to try the Natty test version.
While Natty is not yet finished, it would give you the possibility to test if the live system of Natty works on your laptop. If it does, then you are not closer to understanding the problem, but at least you have a "fix".

EDIT: I understand any frustration a bug like this brings with it. I have tried Linux for years(different distributions and then since Ubuntu 6.X I think) and always reverted back to Windows up until last year. I never had time to fix the small annoyances. But now I don't want to go back to Windows at all. There are still a lot of problems in Linux/Ubuntu which has a lot of different reasons (especially the way most hardware vendors are not supporting Linux at all and not even trying to support the people who do add the support for hardware) and I know it can be annoying and frustrating when you encounter something and it just does not work. But on the other side there are a lot of things which work better and easier in Linux as well and Ubuntu is developing in a pretty fast pace and it will get better and better. All I can say is, that from my point of view, this is all totally worth it.

---

### Post by ClientAlive on 2011-03-22
WAY cool tordeu! You give me hope for humanity.
 
I want to try Natty first; and then, if that doesn't work for me I'll try the fix for 10.10.
 
I'm just not sure which of two of the images I need. You see, I have an AMD Turion 64 in my machine and it allows you to operate in either 32 or 64 bit. I have never had it in 64 bit mode and don't suppose I really want to start now.
 
So is it the "[[COLOR=#772953]PC (Intel x86) desktop CD[/COLOR]]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.iso")" I need or the "[[COLOR=#772953]64-bit PC (AMD64) desktop CD[/COLOR]]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso")" that I need?
 
Jake
;)
 
----------------
 
I'm a dumbass. Sorry. It tells you right there.

---

### Post by uRock on 2011-03-22
Use the AMD64 version. If you need help with Natty, please start a new thread here to get speedy results. [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

Cheers,
uRock

---

### Post by tordeu on 2011-03-22
:D Thanks!

There is always some kind of discussion going on about 64-Bit. It had problems in the past, but it works great now. (I use 64-bit and don't have any 64-bit related problems).

Nevertheless, I would probably still recommend that you take the Intel x86 release, which is the 32-Bit version, and try that. It is the safest option and I don't see any advantage you would get from using the 64-Bit version, although it should not hurt, either. It's really a matter of choice and should not make much of a difference. But if you encounter problems with your choice, you could try the other.

---

### Post by ClientAlive on 2011-03-22
The words you are reading are being typed through fiirefox in Natty live!

Still have some issues to work through like getting my wireless connection to the modem working (I'm plugged in through an ethernet cable right now using the default account  - something "echo" its called). And firefox likes to crash.

This is actually the second boot up of Natty live. It's buggy but if I can get the wireless connection working I'll install. I can live with buggy for a couple mos as long as it's not too bad. Probably a lot that can be done to square things away just by updating things and configuring correctly, etc.

I think what I'll do is re-install windows on my desktop so I have that to fall back on for internet till the laptop is squared away.

Any chance you could help me uderstand the config of wireless in network settings? I have the info I need to fill in the fields here at home but the network settings app in linux has a lot more stuff in it than windows does. Not sure I understand it entirely.

Thanks so much. We did it. Well, mostly.

Jake
:D

PS: Do you think I should close this thread as solved and post elsewhere now? I've never used forums much before this so forum protocol is another thing I need to learn.

Thx

---------------------------------------------------------

The folllowing is the type of information my internet provider was able to give me. If there are places in the network settings where it is needed - it is what I have to use.

  	 	 	 	 	 	  [B][FONT=Times New Roman][SIZE=3]INTERNET
[/SIZE][/FONT][/B][FONT=Times New Roman][SIZE=3]WAN IP:   
WAN Subnet Mask:   
WAN Gateway IP:   
Primary DNS:    
Secondary DNS:    [/SIZE][/FONT] 
  
 [B][FONT=Times New Roman][SIZE=3]GATEWAY
[/SIZE][/FONT][/B][FONT=Times New Roman][SIZE=3]DHCP Gateway IP Address:   
Subnet Mask:   
DNS Proxy IP Address:   [/SIZE][/FONT] 
 [B][FONT=Times New Roman][SIZE=3]INFORMATION
[/SIZE][/FONT][/B][FONT=Times New Roman][SIZE=3]Model Name: 
Software Version: 
Hardware Version: 
RF Cable MAC Address:  
Wireless MAC Address:  
RG WAN MAC Address: 
Serial Num: [/SIZE][/FONT]
 [B][FONT=Times New Roman][SIZE=3]WIRELESS
[/SIZE][/FONT][/B][FONT=Times New Roman][SIZE=3]SSID:   
Encryption Type:   
Encryption length:   
Encryption Default Key:   
Encryption Pass Phrase:   [/SIZE][/FONT]

---

### Post by tordeu on 2011-03-22
Great to hear that Natty live is working on your system.

Most crashes you experience should reduce over the next weeks (Firefox 4, for example, just got release yesterday (or today, depending on what time zone you are in ;)).

And I think it's a good idea to have Windows as a fallback on your PC, so the issue you are having can get resolved and still having another system you might use instead until everything is up and running.

I also think it would be best to mark this thread solved and open a new one for setting up the network. This is also a good idea, so people who know a lot about WiFi might help you as well. I will certainly try to catch your new thread and help you as well as much as I can.

But at least we first step is done. :D

---

### Post by ClientAlive on 2011-03-22
Right on. Thanks brother.

Jake

---

