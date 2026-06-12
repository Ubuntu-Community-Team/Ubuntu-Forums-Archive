---
title: "Why did Vista go into hiding?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by jonivey on 2007-03-18
My new desktop PC has Vista pre-loaded on it. :(  When I installed ubuntu 6.10 and 
restarted, the dual boot screen appeared, from which yours truly attempted to 
highlight Windows Longhorn (Vista).  When I did so, the entire screen went black
and nothing happened for the longest time, so had to power down and power up.
Vista seems to have gone into hiding. I'm told Vista can't be uninstalled. Would 
LOVE to uninstall it, bu-u-t my wife is required by her professor to use MS Word
for her homework.

Can I leave ubuntu on my cptr and just install MS Office?  If so, how?  Tried that,
but ubuntu doesn't seem able to interact with the Office install CD.

Or can I edit the boot loader screen using BASH (??) commands to bring
Vista back from the dead?  If so , how?

Or can someone send me online any of the following OS's, as I'm told
they all work well with Linux: XP (any full version), Windows ME, Win 98?
I assume I'll be able to install Office from within any of those OS's.
   Thanks.

---

### Post by floke on 2007-03-18
you could just use Open Office org and save your wifes work as an MSWord file? The prof will never know.

---

### Post by cookieofdoom on 2007-03-18
I personally love OpenOffice but if you have a need to use Office... VMWare Player or Virtualbox are fairly easy solutions. They actually emulate Windows. If you do a search, there's much more information on it than I can give you. I use it to run a couple of applications myself and just impress friends by running two operating systems at the same time.

---

### Post by nim278 on 2007-03-19
I can definitely vouch for VMWare being a great solution. I took a GIS course a few years ago and used it to run ArcView and software like that fast and painless.

For MS-Word/Excel I purchased Crossover Office ([www.codeweavers.com)](www.codeweavers.com)), though apparently you can use Wine too. Crossover Office lets you run these apps without needing to run the whole OS. They look and act just like Linux apps. The only feature that won't work is VBA macros in your spreadsheets.

M

---

### Post by jonivey on 2007-03-19
Thanks for the 3 responses. I'm inclined to try simpler solutions first, so the
following is directed to Steve K's reply.
My wife's prof insists on Times New Roman font, but it's missing in OpenOffice 2.0.
I just tried to download OO2.1, thinking it MIGHT contain TNR font, but I
don't know how to get 2.1 to replace 2.0.  When I clicked the post-installation
OO2.1 desktop icon:

/home/jonivey/Desktop/OOo_2.1.0_LinuxIntel_install_en-US.tar.gz

it goes to an Archive Manager but I can't get AM to replace 2.0 with 2.1.
Can anyone (anyone at all) help?
Does anyone know if Times New Roman is included in OO2.1?
Thanks.
By the way, why on EARTH would TNR not be included in Open Office??!!??!!??

---

### Post by floke on 2007-03-19
Its in 2.1 yes. I'm looking at it now.
You have to remove the old version before installing the new one if you do it manually.

So remove OOo in synaptic and try installing the new one again.

---

### Post by jonivey on 2007-03-19
Thanks, Steve.  But I'm a newbie so I don't know what you mean by "remove
OpenOffice 2.0 in synaptic"

---

### Post by MJN on 2007-03-19
The **msttcorefonts** package could be just what you're looking for:

```

msttcorefonts - 
Installer for Microsoft TrueType core fonts
This package allows for easy installation of the Microsoft True Type
Core Fonts for the Web including:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

You will need an Internet connection to download these fonts if you
don't already have them.

```Mathew

---

### Post by floke on 2007-03-19
You forgot to give the CLI.

use: sudo apt-get install msttcorefonts 

Not sure if OOo will automatically pick them up though?

---

### Post by MJN on 2007-03-19
It should do - they're basically dumped into /usr/share/fonts/truetype/msttcorefonts hence available for any package to use.

Mathew

---

### Post by jonivey on 2007-03-19
Where do I type the command?
sudo apt-get install msttcorefonts 
How do I pull up a command line, in other words
(if that's what I'm supposed to do)?
(See, I wasn't kidding when I said I'm a newbie:)

---

### Post by nim278 on 2007-03-19
Confirmed. I did not have these installed before, and just did "sudo apt-get install msttcorefonts" and presto, there they are in OoO :)

---

### Post by nim278 on 2007-03-19
In the applications menu under Accessories, open the program "Terminal" .. you type in the command there. Then it will ask you yo enter your password, and should proceed to install it.

---

### Post by jonivey on 2007-03-19
Thanks, but when I did this, here's what I got:
jonivey@jonivey-desktop:~$ sudo apt-get install msttcorefonts 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
jonivey@jonivey-desktop:~$

---

### Post by nim278 on 2007-03-20
Ah, OK, sorry, I didn't think of that. The reason for this is that by default, Ubuntu does not set up access to copyright software (it's all about advocating free software). To enable this, go to the System menu, and under Administration you will find Software Sources.

Check the box that says "Software restricted by copyright or legal issues {multiverse}". While you're there, you may want to enable other sources as well -- they may come in handy in the future.

When you click close, it will ask you to reload the list of available software. Click Reload. When it is done, you should be able to install msttcorefonts without trouble.

Hope this helps!

Maciek

p.s. I am using the beta version of the newer version of Ubuntu, so there is a chance it is slightly different.

---

### Post by jonivey on 2007-03-21
Thanks very much, Maciek! Times New Roman is now installed; in fact, I'm using it right now.
May eternal bliss fill your clothing :)
By the way, just curious, how do you pronounce &#8220;Maciek&#8221;?  It sounds Polish or Czech to me.
Are you male or are you female? In any case, best wishes to you and God bless!!

Jon

---

### Post by jonivey on 2007-03-21
Thanks very much for all those who responded to my plight, especially nim278, Steve K and MJN.
Steve, I found synaptic package manager.
By the way if I decide to uninstall OO 2.0 and then download OO 2.1,
then, under synaptic, should I uninstall:
Word Processing
OR
Word Processing (multiverse)
OR
Word Processing (universe)?

 Jon

---

### Post by floke on 2007-03-21
There's probably a far easier way (maybe sudo aptitude remove openoffice.org) - but you could just check all the boxes listed as packages for openoffice.org for a complete removal. 

Or you could upgrade to Feisty, since this has 2.1 in it by default :) !

Glad it all worked out for you anyways.

** EDIT ** Just checked - it's 2.2, so even better!

---

### Post by jonivey on 2007-03-21
Hi Steve

I just upgraded to Feisty Fawn.

FYI

Jon

---

### Post by floke on 2007-03-21
Go easy there Tiger - it's still Alpha (until tomorrow).
Life on the bleeding edge eh? 

All you need now is Beryl....

:popcorn:

---

### Post by nim278 on 2007-03-22
Hi Jon,

You're very welcome, glad to help! :)
You got it -- Polish. It's "Ma" like in "Mathew" and "ciek" is pronounced kindof like "check" but the ch is a bit of a softer sound. 

Cheers,
Maciek

---

### Post by jonivey on 2007-03-22
Can anyone steer me through setting up Evolution?
Do I choose POP for receiving email, do I choose .....etc, etc.
Note: I just have a home computer (no LAN) and I have Comcast broadband.:confused:

---

### Post by floke on 2007-03-22
REckon you're better off setting up a new thread on this one, since it will get lost here. For what ot's worth though, you could use Thunderbird rather than Evolution, which would save you from using stuff from the sour bunch who cut a deal with MS. I think POP is what you want though - but scout around for instructions.

** EDIT ** PS: How's your missus getting on with the MS fonts?

---

### Post by nim278 on 2007-03-22
Echo to Steve's comments -- post a new thread and you will get a lot more help. But my 2 cents: Evolution (or any other client) is pretty similar in its setup, just that the same options are hiding in different places. Although they don't have instructions specific for Evolution, here is some info from Comcast: [http://www.comcast.net/help/faq/index.jsp?faq=Emailtop17481](http://www.comcast.net/help/faq/index.jsp?faq=Emailtop17481)

It appears you want to use SMTP for outgoing mail and POP3 (POP) for incoming. That site also links to an "E-Mail FAQ", which has step by step instructions for many other programs which could be similar.

Maciek

---

### Post by jonivey on 2007-03-23
Thanks to everyone re Evolution. Due to limited time right now, I'll ask my million-dollar
question and then check back in a day or two to see if anyone responded.
(Evolution is a lower priority.)
Because I had to wipe my HD yesterday in a vain attempt to install Win982E,
when I re-installed Feisty today--- much to my disappointment--- it had OOo2.0,
not OOo2.2, so I downloaded 2.1 from OOo's site,
(didn't see 2.2 there)  but now 2.1 is just a desktop icon.
I tried to use synaptic to uninstall 2.0 but I guess I'll need detailed instructions
on how to uninstall it.
Also I wonder why THIS Feisty download ----
the download lasted about 4 hours (!!!!)--- didn't have 2.2 as previous one did?
Also I have a desktop icon now thusly:

/home/jonivey/Desktop/feisty-desktop-i386.iso

Do I need to do something to complete the changeover to Feisty?

How do I know that the Feisty download did in fact take? (Have already restarted
a number of times). Previously had 6.04. Yesterday was a wild ride---W98,
6.04 etc etc
Would anyone care to shed some light on this?

---

### Post by nim278 on 2007-03-23
I'm not an expert but my best guesses are as follows:

- The download was slow because as a testing release, it's not mirrored on all the other servers other than the official one.
- OoO 2.2 _should_ download if you install Feisty then get all the upgrades. To do this, enable the extra repositories in "Software Sources" like you did before, then in the terminal run "sudo apt-get dist-upgrade" (or do it through synaptic)

I have been running Feisty since near its inception, and I currently have OoO 2.2 installed without having done anything special. Remember, this is beta software so it is still likely to have some kinks in it..

Maciek

---

### Post by nim278 on 2007-03-23
Sorry, I just re-read that. I'm not sure what you did, but I'm not sure if you actually installed Feisty either. May I ask how you installed Edgy to begin with? Or was it Dapper (Edgy = 6.10, Dapper=6.04)?

The .ISO file on your desktop is a CD image. To install feisty you would burn that to a CD, then boot from it. But if you already have Dapper or Edgy installed you won't need to do this -- there is an easier way to upgrade though I'm not sure what it is -- again, I would suggest posting the question in a related forum instead of here.

Maciek

---

### Post by jonivey on 2007-03-23
Steve

How do you set up a new thread? I forgot how.

My wife has had a very hectic schedule and has not really had much experience with OOo
yet. She wanted to use Office but my efforts over the past few days to install an Office-friendly underlying Microsoft OS have been in vain.  So now she has resigned herself to using OO.
(Unless someone can tell me how to install Office into Ubuntu 6.10 or 7.04, which I have no doubt would please her immensely.)

---

### Post by jonivey on 2007-03-23
> **nim278 said:**
> Sorry, I just re-read that. I'm not sure what you did, but I'm not sure if you actually installed Feisty either. May I ask how you installed Edgy to begin with? Or was it Dapper (Edgy = 6.10, Dapper=6.04)?

The .ISO file on your desktop is a CD image. To install feisty you would burn that to a CD, then boot from it. But if you already have Dapper or Edgy installed you won't need to do this -- there is an easier way to upgrade though I'm not sure what it is -- again, I would suggest posting the question in a related forum instead of here.

Maciek
Maciek

Hi. I suspect you're right. Apparently I didn't install 7.04, but merely downloaded it. Now I suppose I have to get a blank CD-RW and burn it and then just boot from CD.
As to your question, I originally installed 6.10 from a CD that Canonical mailed to me.

Jon

---

### Post by nim278 on 2007-03-23
Installing Ubuntu:
You are correct. It should be as simple as put a blank CD in, right click on that file you downloaded, and say "Write to Disc". When you boot from the CD, it will be very similar to how you installed Edgy from the CD you got from Canonical.

To set up a new thread:
Starting at the ubuntuforums.org home page, find the forum relevant to the question you want to ask. At the top of the list of threads in the forum, there is a "Forum Tools" link, when you click on it, you will get a drop down menu where "Post a New Thread" is an option.

Office in Ubuntu:
There are 3 ways (that I am somewhat familiar with).
1. Purchase Crossover Linux ([http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)) for about $50. This is what I did. It was very easy to install and products like Excel and Word 2003 work seamlessly within Linux, as do a lot of other Windows apps.

2. Use Wine. Wine is the free open source software that Crossover is based on, however it takes a bit more elbow grease to get it going. I've only heard of success with older versions like Office 2000. [http://frankscorner.org/index.php?p=office2000](http://frankscorner.org/index.php?p=office2000)

3. Emulate Windows running inside Ubuntu. A little bit slower depending on your computer, but you can run anything perfectlky. This would actually be the entire Windows OS running inside your Ubuntu. There are a lot of instructions though so you have to be careful. It works better with XP than Vista (so I hear).
[http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631)
OR
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by jonivey on 2007-03-27
Help!!
I not only couldn't install Feisty from the CD I burned:
"Step 5 Prepare disk space"
didn't work in either Manual (no manipulable click places)


]
(hope that wasn't too technical:) 
OR in "Guided -use entire disk" mode:
the forward button was inoperable.

AND
when I typed
sudo apt-get update
and
sudo apt-get install debconf ubiquity
THAT didn't do any good at all
and now  I've decided to go back temporarily
to Ubuntu 6.10.

Is there another iteration of 7.04 online somewhere that could be downloaded
that does NOT have these problems?

On a separate note, I tried to install a fax machine driver from a CD, but got this msg:

Cannot open /media/cdrom0/Setup.exe: No application suitable for automatic installation is available for handling this kind of file

Tried Software Sources 
but already the box for copyrighted SW (indeed ALL) boxes are checked. )

---

### Post by jonivey on 2007-03-27
Thanks Maciek

Gee, my confidence level is suffering lately due to Feisty install problems and the issue with Evolution, so I'll buffer your helpful suggestions re Office in Ubuntu and try them out later.
Right now I'm dealing with pressing matters like a job search and car trouble.

Jon

---

### Post by jfinkels on 2007-03-27
> **jonivey said:**
> [...]I don't know how to get 2.1 to replace 2.0[...]

I hate to toot my own horn, buuut...

I posted this how-to just the other day, in case you want to take a look at installing OpenOffice.org 2.1. [http://www.ubuntuforums.org/showthread.php?t=392735](http://www.ubuntuforums.org/showthread.php?t=392735)

It's aimed at beginners.

If you've already found a simpler solution (which I'm pretty sure one of these other people may have suggested) then don't worry about it! :D Good luck.

EDIT:

p.s. I suggest sticking with Ubuntu 6.10, for now.

---

### Post by jonivey on 2007-04-08
Hi
I tried to use your instructions to install OOo2.1 (ended up deciding to download 2.2 not 2.1)
but I'm stuck and can't complete Step 4.
Using Nautilus 2.16.1 was able to see about 30 icons of OO, including:
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/jre-6-linux-i586.rpm
AND
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core01-2.2.0-9134.i586.rpm
AND
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-gnome-integration-2.2.0-9134.i586.rpm
but can't figure out what to do next.

Also tried using a terminal but got the following:
jonivey@jonivey-desktop:~$ cd OOF680_m14_native_packed-1_en-US.9134
bash: cd: OOF680_m14_native_packed-1_en-US.9134: No such file or directory
jonivey@jonivey-desktop:~$ cd RPMS/
bash: cd: RPMS/: No such file or directory
jonivey@jonivey-desktop:~$ sudo alien -d *.rpm
Password:
File "*.rpm" not found.
jonivey@jonivey-desktop:~$ 

How do I know which directory to change to using the cd command??

Would you be so kind as to steer this newbie in the right direction?
Thanks.  (I need OOo because I'm trying to shop my screenplay to Hollywood).

---

### Post by jfinkels on 2007-04-08
> **jonivey said:**
> Hi
I tried to use your instructions to install OOo2.1 (ended up deciding to download 2.2 not 2.1)
but I'm stuck and can't complete Step 4.
Using Nautilus 2.16.1 was able to see about 30 icons of OO, including:
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/jre-6-linux-i586.rpm
AND
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-core01-2.2.0-9134.i586.rpm
AND
/home/jonivey/Desktop/OOF680_m14_native_packed-1_en-US.9134/RPMS/openoffice.org-gnome-integration-2.2.0-9134.i586.rpm
but can't figure out what to do next.

Also tried using a terminal but got the following:
jonivey@jonivey-desktop:~$ cd OOF680_m14_native_packed-1_en-US.9134
bash: cd: OOF680_m14_native_packed-1_en-US.9134: No such file or directory
jonivey@jonivey-desktop:~$ cd RPMS/
bash: cd: RPMS/: No such file or directory
jonivey@jonivey-desktop:~$ sudo alien -d *.rpm
Password:
File "*.rpm" not found.
jonivey@jonivey-desktop:~$ 

How do I know which directory to change to using the cd command??

Would you be so kind as to steer this newbie in the right direction?
Thanks.  (I need OOo because I'm trying to shop my screenplay to Hollywood).

Hello, friend. Take a look here for a howto for 2.2: [http://ubuntuforums.org/showthread.php?t=398074](http://ubuntuforums.org/showthread.php?t=398074) .

Just so that you understand what's going on with those commands, *cd* means "_c_hange _d_irectory". You can think of it like taking a walk through your filesystem, room by room (each room is a directory). So when you download the OpenOffice.org package, you have to change to the directory in which you downloaded it, then run the *tar* command (which just unpacks the installation files from an archive), the *alien* command, etc.

If you need any more help, please post in the thread to which I referred you ([http://ubuntuforums.org/showthread.php?t=398074)](http://ubuntuforums.org/showthread.php?t=398074)).

---

