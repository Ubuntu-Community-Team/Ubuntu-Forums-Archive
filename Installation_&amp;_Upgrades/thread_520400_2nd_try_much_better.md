---
title: "2nd try much better"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by CD Baric on 2007-08-08
OK - I have installed Ubuntu 7.04 on a brand new machine:

AMD 6000+ Dual Core CPU
4 gig memory
2 x 500gig sata drives
nVidia dual DVI video

This is a dual boot system with XP Pro on the first HD and Ubuntu on the 2nd.

Everything is installed and I have 1680 X 1050 video, HiDef sound, networking, usb ports, 1394 ports, DVD burner, floppy, etc.

Here are my questions:

(1) What is the root/su password?

(2) Where do I get the libdvdcss file?

(3) How do I install nVidia proprietary video drivers?

(4) How do I get a package so I can write to my NTFS file system?

(5) How do I modify the kernel for 4 gig memory?

Thanks

CD 'Bar' Baric

---

### Post by jim_p on 2007-08-08
1) To set the root password open up a terminal and write ```
sudo passwd
``` 
You will be prompted for the root password
(I am sure i am missing something here)

2)Open up Synaptic, search for it and install it. Just in case you dont get any results, make sure you have the restricted/universe/multiverse sources enabled. These are found in "Settings > Repositories"

3)Search for nvidia-glx in Synaptic and install them

4)Search for ntfs-3g in Synaptic and install them

---

### Post by CD Baric on 2007-08-08
> **jim_p said:**
> 1) To set the root password open up a terminal and write ```
sudo passwd
``` 
You will be prompted for the root password
(I am sure i am missing something here)

2)Open up Synaptic, search for it and install it. Just in case you dont get any results, make sure you have the restricted/universe/multiverse sources enabled. These are found in "Settings > Repositories"

3)Search for nvidia-glx in Synaptic and install them

4)Search for ntfs-3g in Synaptic and install them

Thanks for your reply!

The thing you forgot in answer one was:

sudo passwd root

Unfortunately root seems to be pretty useless.

(2) Can't find 'settings repositories' Have still not found libdvdcss package.

(3)  That didn't work. It pooched the install.

(4) Never got that far - the installation was pooched trying to install nVidia binary drivers.

I am really going to have to give up on Ubuntu, at least for now - it is too difficult to do even ordinary chores that a real root account in a real Linux OS can do.

I never did get an answer about recompiling the stock kernel to include 4 gigabyte memory - that means I waste almost a gigabyte of memory. This is a simple procedure in Slackware..

All I can say is 'Keeping Trying'!

CD 'Bar' Baric

---

### Post by jim_p on 2007-08-09
Oh :(
 I am sorry to hear that you  broke the install.
About the nvidia drivers, can you enter your system using the recovery mode?
Its the 2nd entry you see at the grub menu (the OS selection screen 
before proceeding to loading ubuntu).
If so, you can alter the  **/etc/X11/xorg.conf** file and replace every "nvidia" with "nv". 
This will restore your xsystem to its original state (you will see desktop, icons, etc) using a typical driver. After booting in your xsystem you can install the drivers from the "Restricted Drivers Manager".

I forgot that because I am using 6.06LTS and there is no "Restricted Drivers Manager" for me.

Please tell me if you have done it so I can guide you through the rest. Thank you.

---

### Post by CD Baric on 2007-08-09
I need to know where to find libdvdcs

WHERE IS IT?

Thank

---

### Post by logos34 on 2007-08-09
add Medibuntu to your repos sources.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by CD Baric on 2007-08-09
OK - That didn't work.

Why is this so Fsking hard???

Your repo was rejected!

Are you SURE you know what you are doing?

---

### Post by merlinus on 2007-08-09
Did you actually take the time to read the information on the page that logos34 posted the link for?

Also, a simple google search turned this up:

[http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html)

Your attitude leaves a great deal to be desired.  This is an all-volunteer forum, and perhaps you can find paid support someplace, if you are dissatisfied.

Of course, you might simply follow your own advice from your earlier post, and use a real linux OS!

:guitar:

-merlin

---

### Post by CD Baric on 2007-08-09
I am sorry if I have  an attitude BUT I am getting some bad information here..

logos34 SPECIFICALLY SAID:

"add Medibuntu to your repos sources.
https://help.ubuntu.com/community/Medibuntu"

So I tried to add "https://help.ubuntu.com/community/Medibuntu" to my repositories sources.

WAS I WRONG to follow his instructions to the letter?

Now YOU tell me to READ what it says there - FINE! I will do that AND I will follow the instructions on that page.

So tell me - how is my mother/father/uncle supposed to find and install this NEEDED library if you guys intentionally hide it???

It is WRONG not to have this stuff (libdvdcss, mp3 and all the other codecs required for life in the 21st century) available for installation, especially in Canada where we aren't living under the heel of media stakeholders.

CD 'Bar' Baric

---

### Post by merlinus on 2007-08-09
Here is a quote from the beginning of the medibuntu page:

**Introduction**

  [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Medibuntu]("http://www.medibuntu.org/") (**M**ultimedia, **E**ntertainment & **D**istractions **I**n U**buntu**) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc). 
 Some of these packages include the [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] libdvdcss]("http://www.videolan.org/developers/libdvdcss.html") package from [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] VideoLAN]("http://www.videolan.org/") and the external binary codecs package (commonly known as w32codecs) used by [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] MPlayer]("http://www.mplayerhq.hu/") and [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] xine]("http://xinehq.de/"). 
  **Disclaimer**

  Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 
 See Ubuntu's [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Free Software Philosophy]("http://www.ubuntu.com/ubuntu/philosophy") and the [FreeFormats]("https://help.ubuntu.com/community/FreeFormats") page for a more comprehensive discussion of these issues. 
  

---

### Post by merlinus on 2007-08-09
Also, a simple google search will turn up the webpages for these various software packages that cannot be included in ubuntu for the aforementioned reasons.

And usually with installation instructions as well.

-merlin

---

### Post by CD Baric on 2007-08-09
Yes, I read it and it clearly states:

"if you own a legally-purchased DVD and are trying to play it on your own computer with Ubuntu, using libdvdcss is legal because you are merely exercising the license that you acquired when you obtained the DVD."

Perhaps the next Ubuntu version should be called "Gutless Weenie"!

I live in Canada - The Land Above The Land Of The Free (What a joke that is)

CD 'Bar' Baric

---

### Post by CD Baric on 2007-08-09
> **merlinus said:**
> Also, a simple google search will turn up the webpages for these various software packages that cannot be included in ubuntu for the aforementioned reasons.

And usually with installation instructions as well.

-merlin

Yeah, well, Silly Me asking for help in the... ahhhh.... erm...  Ubunto Help Forums!

Yes sir, I understand how that would put you off.

That and my bad attitude.

CD 'Bar' Baric

---

### Post by merlinus on 2007-08-09
From what I can see, you received the assistance requested.

Perhaps it did not come in the form that you desired, but such is life.

You were unwilling to do anything for yourself, such as read webpages and search google and elsewhere, but demanded to be spoon-fed and cried when you were not.

Nastiness and contempt only breed more of the same.

Best of luck.

-merlin

---

### Post by Pumalite on 2007-08-09
Ditto.

---

### Post by CD Baric on 2007-08-10
> **merlinus said:**
> From what I can see, you received the assistance requested.

Perhaps it did not come in the form that you desired, but such is life.

You were unwilling to do anything for yourself, such as read webpages and search google and elsewhere, but demanded to be spoon-fed and cried when you were not.

Nastiness and contempt only breed more of the same.

Best of luck.

-merlin

Climb down off the cross - you look silly.

YES I eventually puzzled out the libdvdcss issue and even the low resolution video screen issue and a few other things that I haven't mentioned.

What I am saying is THE INSTALLATION OF REQUIRED LIBS AND CODECS SHOULD BE A ONE CLICK PROCESS! No?

I can't recommend Ubuntu to any of my Windows using friends and family because the first thing they are going to do is drop in a DVD they own or rented and BLAMO - end of the great Linux experiment.

Ubuntu is only going to work for experienced Linux users - and even we may get just a little excited about how difficult this COMMUNITY EFFORT has made such a simple task.

The problem is YOU don't seem to like the feedback, no matter how justified it is.

Don't make the claim that Ubuntu is noob friendly WHEN IT ISN'T! That just leaves a bad taste in the mouth of every Windows user who gives Ubuntu a go.

CD 'Bar' Baric

---

### Post by jim_p on 2007-08-10
Well, I have this line set as my medibuntu repo

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

so I suppose yours will be feisty instead of dapper :)



p.s. I should have enclosed it in a "code" rectangle but the buttons above dont work

---

### Post by CD Baric on 2007-08-10
> **jim_p said:**
> Well, I have this line set as my medibuntu repo

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

so I suppose yours will be feisty instead of dapper :)



p.s. I should have enclosed it in a "code" rectangle but the buttons above dont work

No... that is great.

Succinct and to the point.

Thank you.

CD 'Bar' Baric

---

### Post by jim_p on 2007-08-10
Look what I found! Its about installing a kernel with support for more than 4GB of RAM!!

[http://www.skolelinux.no/~klaus/sarge/x2003.html](http://www.skolelinux.no/~klaus/sarge/x2003.html)

I know it does not mention ubuntu anywhere, but i did the whole procedure on my pc, besides 
installing, and it works!

---

### Post by CD Baric on 2007-08-10
> **jim_p said:**
> Look what I found! Its about installing a kernel with support for more than 4GB of RAM!!

[http://www.skolelinux.no/~klaus/sarge/x2003.html](http://www.skolelinux.no/~klaus/sarge/x2003.html)

I know it does not mention ubuntu anywhere, but i did the whole procedure on my pc, besides 
installing, and it works!

Great!

You see, I don't have a clue yet what can and can't be done on Ubuntu - I am still learning the ropes. Perhaps I will find a website that deals with experienced Linux users trying Ubuntu for the first time.

Thanks

CD 'Bar' Baric

---

### Post by Odrodzona-Sarmacja on 2007-08-10
From what I know you can't run Ubuntu gui as superuser, but you can run programs like for example file browser with superuser (root) rights. Try in terminal:

>gksudo <program_name>

About legalities of multiverse's software... Don't worry about these license extortionists, just use the software, because that's what it is for. But if you really worry about these legalities, then join Pirate Party of your nation and kick some thieving ***... the hard way from which they can't buy or lobby themselves out... at the ballot-box.

---

### Post by CD Baric on 2007-08-12
> **Odrodzona-Sarmacja said:**
> From what I know you can't run Ubuntu gui as superuser, but you can run programs like for example file browser with superuser (root) rights. Try in terminal:

>gksudo <program_name>

About legalities of multiverse's software... Don't worry about these license extortionists, just use the software, because that's what it is for. But if you really worry about these legalities, then join Pirate Party of your nation and kick some thieving ***... the hard way from which they can't buy or lobby themselves out... at the ballot-box.

Sorry for delay - has been a busy weekend.

I live in Canada so I am not concerned about supposed IP claims originating from the USA.

Thanks for the help.

CD Baric

---

