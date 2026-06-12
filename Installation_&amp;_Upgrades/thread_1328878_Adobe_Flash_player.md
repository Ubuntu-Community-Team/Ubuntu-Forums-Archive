---
title: "Adobe Flash player"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by jeri on 2009-11-16
I am running Ubuntu 9.1 from a usb flash drive...I love it....it was working great until I went on a couple websites that required adobe flash player....it directed me to the site and there was an option for my this OS.  I attempted to download and install and it said it could not open file.  Then it said it was inconsistent and asked me to remove it so I did.  Now when I go to Updates it says the adobe flash is there and inconsistent.  I let it remove it again and it said to reinstall manually.  I need help...I don't know how to do this.  I would appreciate any assistance anyone could give me.

Thanks,
Jeri;)

---

### Post by 1roxtar on 2009-11-16
With Ubuntu 9.10, I installed the Ubuntu-Restricted-Extras and it automatically installed Adobe Flash Player.

---

### Post by jeri on 2009-11-16
Thanks for the reply.  I will certainly try that and let you know.

Thanks again,
Jeri

---

### Post by garvinrick4 on 2009-11-16
Without Ubuntu-restricted-extra's you canna notta do a nothin in Media. It gives you
your codec's for video in gives your flash player it even gives you the Microsoft core fonts,
True type fonts. So I agree with 1roxtar.

---

### Post by jeri on 2009-11-16
Well I tried and this is what I got:
The requested URI "apt:ubuntu-restricted-extras" is invalid
Unable to load page

Any help is appreciated.

Thanks,
Jeri

PS,,,,,, is this something I need to pay for...but I didn't get an option for that.

---

### Post by garvinrick4 on 2009-11-16
Open a terminal:  Applications to Accessories to Terminal

sudo apt-get remove flashplugin-nonfree

sudo apt-get clean

sudo apt-get install flashplugin-nonfree

sudo apt-get update

sudo apt-get install ubuntu-restricted-extras

sudo apt-get update

Type these commands in one at a time and press enter after each one. 
Will ask for password. Give it to them, will not see letters for password

I do not know if you have the ubuntu-restricted-extras
you can actually just install them at the code:  sudo apt-get install flashplugin-nonfree

---

### Post by 1roxtar on 2009-11-17
> **jeri said:**
> Well I tried and this is what I got:
The requested URI "apt:ubuntu-restricted-extras" is invalid
Unable to load page

Any help is appreciated.

Thanks,
Jeri

PS,,,,,, is this something I need to pay for...but I didn't get an option for that.

You can get it from the Ubuntu Software Center.  Go to Applications/Ubuntu Software Center and type "ubuntu-restricted-extras" in the search bar....and it's FREE!!!
:guitar:

---

### Post by garvinrick4 on 2009-11-17
run in Terminal.

sudo gedit /etc/apt/sources.list 


Look in list that opens and make sure you have this.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

If not you have to copy and paste the line starting with deb
to Software Sources to other software tab to ADD and past it
in APT line click add source and close.

While in Other Software tab make sure disbled on upgrade to karmic
and disabled on upgrade to karmic non-free   are checked.

close and will be added to repositories.

Go to Terminal Code:   sudo apt-get upgrade

Now add your software.

---

### Post by 1roxtar on 2009-11-17
^^^^then with your left hand, tap the top of your head and with your right hand rub your tummy simultaneously, then try walking and chewing gum at the same time.....or just go to the Ubuntu Software Center.

---

### Post by garvinrick4 on 2009-11-17
Mr. 1roxtar,
 I took for granted he tried that. Sometimes other people read these Forums and
want to learn the same way we all did by reading and putting it to practice. 
I hope all he had to do was go to any of the GUI sources and install. But it is nice
to try and learn the command line. I read another Forum where it said SOLVED had
to have karmic partners. So I pass it on. Life is to short to "rub your belly and pat your
head" before you know it you are not so young anymore and no NOTHING. The world is
full of them, tis a pity.

---

### Post by jeri on 2009-11-17
Thanks to everyone who have posted.  I just got online again tonight.  Last evening I was getting too ill to continue....turns out I have H1N1 virus but I am going to try EVERYTHING that all of you generously posted and then I will report back.  Thank you all soooooooo very much.  I'll be back.

Jeri:p

---

### Post by jeri on 2009-11-17
Ok.ubuntu@ubuntu:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US               
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [37.1kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [14.2kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [14B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [5,835B]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [4,677B]    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [72.5kB]         
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [1,165B]   
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [36.6kB]     
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources [24.6kB]          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources [14B]       
Fetched 5,564kB in 18s (295kB/s)                                               
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Reading package lists... Done
ubuntu@ubuntu:~$ sudo gedit /etc/apt/sources.list
sudo apt-get upgrade


..I attempted everything in the order you guys posted. When I attempt to reinstall, it says it is in an inconsistent state.  It won't let me reinstall.  It wants me to manually fix the package.  When I pulled up the index, I saw all the files for it so I think it was installed.   Here is what I got in the terminal and if you have the time, please let me know what you think or if there is something else I could, let me know.  Again, thank you so much.

Jeri:D

---

### Post by garvinrick4 on 2009-11-17
I do not believe I saw this included in your list.
Go to software sources again. The Other Software tap.
MAKE SURE disabled on upgrade to karmic and disabled on to
upgrade to karmic free non-free are checked.

Okay hit ADD: Then copy and paste this line below into APT line:
Click add source.  Close it will add. The go to Terminal and do.
 Code:    sudo apt-get update



deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

Now clean and install will work this time. There is always a fix.
Let me no.

To clean    Code:     sudo apt-get clean

                Code:     sudo apt-get install unbuntu-restricted-extras

                Code:     sudo apt-get update

---

### Post by jeri on 2009-11-17
When I went to Other Software tab, there was nothing there at all..it was a blank page.  I then went to add and copy/pasted the line and add source was not highlighted.  My only option was to cancel.  SO I didn't do the next thing.  Do you think this installation of ubuntu on my usb stick is just incomplete and needs redone.  Do you think it's better to run it off the hard drive instead???   Is there something else I can try to resolve this.  I love running it off the stick.  It runs well except for this little problem.

Jeri

---

### Post by garvinrick4 on 2009-11-17
[Using APT - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto")

[[all variants] Improving Ubuntu: A Beginners Guide to Filing Bug Reports - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1011078") 

[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide") 

[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 

[Illustrated Dual Boot Site]("http://members.iinet.net.au/%7Eherman546/index.html") 

[Ubuntu Geek | Ubuntu Linux Tutorials,Howtos,Tips & News | Intrepid,Jaunty,Karmic]("http://www.ubuntugeek.com/") 

[Dual-Boot Windows 7 and Ubuntu in Perfect Harmony - windows 7 - Lifehacker]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?skyline=true&s=i") 

[Ubuntu:Karmic -]("http://ubuntuguide.org/wiki/Ubuntu:Karmic") 

I do not believe you got the whole package on the Thumb Drive.

In the last link Ubuntu:Karmic' there is instructions on command line installations
of your partners repository.
And I imagine you have to try to get the package Synaptics and Software sources cleaned up I mean get the whole package.

Here are other links for WUBI which is real good to learn Ubuntu with.
And other means of installing Ubuntu.
And some good sites to study.
If you need help let me know.  If you want to install at command line give it a whirl.

---

### Post by jeri on 2009-11-17
I will go to all these sites...thanks for listing them.  But I do plan to redo this stick.  Hopefully that will resolve it.  Before I do, I'm going to try it on my other notebook and see how it reacts.  I want to rule out any hardware conflicts.  I will keep you posted.  You've been so kind.  I appreciate all the time you spent with me tonight.  Should I regard this as solved for now???  I wasn't sure what to do about that.

Thanks again,
Jeri;)

---

### Post by jeri on 2009-11-17
How do you think Ubuntu compares with Linux Mint???  I think Linux Mint is Ubuntu?

Jeri;)

---

### Post by garvinrick4 on 2009-11-18
No not solved yet.  Put a new image on your Flash drive and lets see what pops up.
Synaptic and its Software sources being blank is not to good. 

I like Ubuntu. There are 100's of distro's for Linux out there. This one is just the one
I choose and it is well maintained.

There are some other nice ones. When you read more about Linux and you will they will
all pop up in the articles. Have a nice evening. 

There is always someone willing to help in these Forums.

Post on this Thread your outcome or if you need assistance. I will do what I can and if
I cannot will point you to someone who can. Lot of smart people around here a lot more
accomplished than I. I hope you can put a SOLVED on this shortly.

---

### Post by jeri on 2009-11-18
I did use this stick on a different computer and of course that wasn't the issue.  I haven't re-installed the stick yet,  After working all day on sick computers, I'm kind of fried so I probably won't reinstall this usb drive tonight.  So I am leaving this pending if that is an option.  Thanks again and I will report back.  This forum is wonderful and I truly appreciate all the assistance I received.

Jeri:)

---

### Post by jeri on 2009-11-22
Hi Everyone.........I have wonderful news!!  I created another stick with Ubunti 9.1 and it works fine....even adobe flash player and the update manager works as well and also the snyaptic package manager.  I am a happy camper....:p:).  Thanks to everyone who tried to help....I guess it was just a bad installation for one reason or another.  But I love this OS...it is fast and efficient and hopefully it will continue to run well.  This is a great forum with lots of good and knowledgeable people.  Consider this problem SOLVED!!!

Happy Turkey day,
Jeri:D

---

