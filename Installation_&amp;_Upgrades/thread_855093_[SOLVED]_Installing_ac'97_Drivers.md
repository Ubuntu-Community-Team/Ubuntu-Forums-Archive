---
title: "[SOLVED] Installing ac'97 Drivers"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by xx.canes.rites on 2008-07-10
Ok so after my friends Windows computer was ridden with viruses, I've finally convinced him to switch over to Ubuntu so that he can run a more stable OS, but theres a problem....I CAN"T GET HIS SOUND WORKING! Ok so he has what seems to be an Audigy sound card which is supported under Realtek 97'ac driver but I have no idea how to install his drivers on Ubuntu.

Please don't tell me about Alsa because all his Alsa drivers are installed and they don't work. All I want to know is how to install the ac'97 linux drivers. Realtek has a linux supported driver download but when I download the tar.bz file I have no idea how to install it, so all I want to know is how do I install that driver. The terminal just super confuses me, I'm used to Windows where all you do is download and click on it, then it installs the rest for me, but with Ubuntu they always make me jump through hoops just to install the most simplistic files. Plz help :0

---

### Post by PmDematagoda on 2008-07-10
The AC'97 driver is built-in to the kernel so it should work out-of-the-box, do you see a little cross next to the volume control applet?

---

### Post by xx.canes.rites on 2008-07-10
I'm not at his house on his compute r so I can't know for sure, all I want to know is even if it's not included, lets just say I have a tar.bz file and its a completely different driver from whats included in the kernel, how do I install it. I'm sersiously about to just buy windows again and switch back over, it seems like everyone has to be a developer just to use a linux based oS

---

### Post by xx.canes.rites on 2008-07-10
Ok this is the website with teh actual driver I need for my Friend's computer. [http://sourceforge.net/docman/display_doc.php?docid=9091&group_id=44773](http://sourceforge.net/docman/display_doc.php?docid=9091&group_id=44773) Its for the emu10k1 file, but I have no idea how to install this thing onto his computer.

---

### Post by xx.canes.rites on 2008-07-10
Anyone know how to install tar files from scratch? I need to install that emu10k1 file.

---

### Post by avtolle on 2008-07-10
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) should help you out.

---

### Post by xx.canes.rites on 2008-07-10
Yo thanks let me try it

---

### Post by xx.canes.rites on 2008-07-10
Nope, It tells me I need compiler tools and dependencies both of which I don't know I even have. I only downloaded the tar.bz file from the site above and now I just want to install the darn thing! I click on the install file inside the tar.bz file but nope, it installs everything into the wrong locations and just give me errors.

---

### Post by avtolle on 2008-07-10
Did you download build-essential from the repositories befroe beginning? That is necessary to compile from source, regardless of any other dependencies.

---

### Post by xx.canes.rites on 2008-07-10
Yo the site isnt listed in my repositories, how do I do that? how can I manually add these sites to my repositories.Yo better yet, can you just name a Class I can take at my local college so I can just learn how to use Linux, I hate windows but Linux OSes really don't give much alternative to a better experience for transition users. I'm about to toss this computer out my window LOL

---

### Post by jumponskis on 2008-07-10
it would be much easier on your self to reinstall ubuntu and to make sure u choose the repositories... but if u want to spend money on college courses.... it does defeat the purpose of open-source software if you are going to pay to learn about it...:lolflag:

---

### Post by avtolle on 2008-07-10
Go to the terminal (Applications>>Accessories>>Terminal) and use the following code```
sudo aptitude update && sudo aptitude install build-essential
```

---

### Post by xx.canes.rites on 2008-07-10
I don't know how to choose the repositories is what I'm saying, and every time I ask for help in forums no one answers my questions they just keep telling me a million different options. I'd rather take a class and pay for it, or have my government pay for it then keep on staring at an Operating System that I can't even use because I have no idea what I'm doing on this thing. Ok say I didn't have to pay for the class, which one would I have to take to learn about linux systems ?

---

### Post by avtolle on 2008-07-10
On enabling the repositories, do this; go to System>>Administration>>Software Sources and see what repositories are checked. Check any additional sources you think you will need (don't check the proposed one). Then, reload the sources when prompted.

---

### Post by jumponskis on 2008-07-10
yo about what you just said, checking the sources thing this is a little off the subject but i was curious so I went there and uncheked hardy-proposed (why?) but the hardy backports one was check whats that? (and why was it checked) and why can't i check the box that says important security updates?  That has me a little worried

---

### Post by xx.canes.rites on 2008-07-10
Yo I love the fact that linux is secure and whatnot, but doing simple things on a Linux based OS is seriously annoying the crap out of me. I mean seriously, how long has linux been around and there isn't even an automated installer program, that's sad. Well there is add/remove but there isn't a global automated installer for all files on Linux like there is on Windows.I hate Windows but If people like me can't use linux what other choice do we have besides Windows?

---

### Post by jumponskis on 2008-07-10
> **xx.canes.rites said:**
> Yo I love the fact that linux is secure and whatnot, but doing simple things on a Linux based OS is seriously annoying the crap out of me. I mean seriously, how long has linux been around and there isn't even an automated installer program, that's sad. Well there is add/remove but there isn't a global automated installer for all files on Linux like there is on Windows.I hate Windows but If people like me can't use linux what other choice do we have besides Windows?

there is an automated installer.  In-fact, there are several different package managers you can use if you wanted.  But the easiest is synaptic package manager.  Go to system>administration>synaptic package manager.  There is a search functionality in the program and the programs are also categorized on the left side.  Tar files are an exception, just like windows doesn't automatically download and unzip a zip file, you must select where and with what you want to extract the file with.  Don't complain just because you haven't searched the forums hard enough.

---

### Post by xx.canes.rites on 2008-07-10
windows does unzip zip files...you can choose to download something like winzip or winrar but the actual windows does unzip files and then you just click the .exe and it does the rest for you.Linux on the other hand once you download the tar.bz file your stuck, everyone keeps telling me get repositories, deb files, packagebuilder blah blah blah but where the hell do I get these files, all I have is the tar.bz file and it has the drivers I need to install within that file. Yet I can't install the darn things to save my life. The tar file isn't in synaptic, i tried sudo apt-get way of doing it and it installs the files into wrong paths and gives me errors, so tell me mr fancy pants what do I do now? I'm trying to give Ubuntu a chance and see its plus positives but so far no good. When you can't install needed files to hear the sound then whats the point of even having open source if you can't even get the darn thing working. I'd rather pay for something that works, then not pay for something that doesn't. But again im here trying, but to no avail. All I wanted to know was how to install the darn file and no one seems to know...

---

### Post by jumponskis on 2008-07-10
if you want people to help you, you should also not call them names like a 3rd grader.

---

### Post by xx.canes.rites on 2008-07-10
i found the creative labs File i needed and I posted the website that gave me the linux platform driver...zzzzzzzzzz.... its the emu10k1 file but its all .tar file so what do I do now, you have to understand I am seriously a 2 day old Linux users, I have no idea what these command lines mean. You have to be patient and explain things to me just like any other windows user that switches over. How do people expect windows users to switch over into a place they are not familiar with and then get spoken to in an unfamiliar language(Terminal language). Its like speaking spanish to an englishman, he has no idea what you're saying.

---

### Post by xx.canes.rites on 2008-07-10
> **jumponskis said:**
> if you want people to help you, you should also not call them names like a 3rd grader.

First of all I didn't call anyone a third grader, second of all third grader isn't a derogatory remark, anyone in school is doing the right thing. Third of all heres the website with the file I need [http://sourceforge.net/docman/displa...group_id=44773](http://sourceforge.net/docman/displa...group_id=44773)

---

### Post by jumponskis on 2008-07-10
> **xx.canes.rites said:**
> i found the creative labs File i needed and I posted the website that gave me the linux platform driver...zzzzzzzzzz.... its the emu10k1 file but its all .tar file so what do I do now, you have to understand I am seriously a 2 day old Linux users, I have no idea what these command lines mean. You have to be patient and explain things to me just like any other windows user that switches over. How do people expect windows users to switch over into a place they are not familiar with and then get spoken to in an unfamiliar language(Terminal language). Its like speaking spanish to an englishman, he has no idea what you're saying.

I know where your coming from and I apologize for being ignorant and not reading the entire thread.  Your situation is not commonplace.  Most programs and files on ubuntu do not com in a tar container.  People do not like them.  And some people use them to contain highly compressed data (aka: Tar Bomb)  When seemingly small file is extracted it decompresses into hundreds of GB of data filing the users hard-drive.  Something,  I visited the page you posted.  This is much to complicated and NO *normal* ubuntu user would go through all this.  I recommend visiting this site: [http://alsa.opensrc.org/index.php/Emu10k1](http://alsa.opensrc.org/index.php/Emu10k1)  don't be put off by the word alsa, just visit the site.

---

### Post by xx.canes.rites on 2008-07-10
ok im off to the website to try this option.

---

### Post by jumponskis on 2008-07-10
also go to synaptic and search alsa.  select the fisrst package and also scroll down and select the package that says alsa tools and alsa tools GUI.  Alsa tools has an Emu10k1 compiler which should be of enormous help.  this link contains a link for all alsa-supported creative labs cards.  Yours is listed.  [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)  But there are no audigy cards that run 10k1, they are all either on 10k2 or a completely different driver.  You should probably look at this.  It also looks like you will only be able to utilize analog input/output but this is not an issue with ubuntu.  This is an issue with compatibility problems.  It seems that soudblaster and ubuntu go together like windows software and older mac operating systems.

---

### Post by jumponskis on 2008-07-10
If you can't settle for analog sound (I know I would be kinda ticked off)
then visit this link [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1) and select 3. _Introduction for Creative EMU based soundcard_ it is a much simpler way to go about what you were doing before, but you will still need to use the terminal (Alt+F2).  I have no further suggestions beyond this, I only started 10 days ago.

---

### Post by jumponskis on 2008-07-10
also if the computer your running is a dell visit this page [http://alsa.opensrc.org/index.php/Emu10k1x](http://alsa.opensrc.org/index.php/Emu10k1x)  because then you have a whole new set of problems

---

### Post by xx.canes.rites on 2008-07-10
Yo big help, All my sound is working fine I only need to know about these drivers because I installed Ubuntu on my friends computer and he's freaking out cause his sound wasnt working haha and when they gave me tar files I was completely stumped but you have been a huge help and I think I can take it over from here thanks man.

---

### Post by jumponskis on 2008-07-10
Glad I could help.  Please remember to mark this thread as solved.

---

