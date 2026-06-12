---
title: "what to type in the terminal to install google chrome browser on an offline computer?"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by newbie14 on 2015-04-10
I have copied the google-chrome-stable_current_i386.deb file from a flash drive to the home folder of my offline ubuntu computer at my home.
I want to install this google chrome program on my offline ubuntu computer.
[ATTACH=CONFIG]261206[/ATTACH]
My mouse device is broken.
What should I type in the terminal program to install this google chrome program?
edit 1: I installed the ubuntu to the flash drive using this tutorial:
[http://ubuntuforums.org/showthread.php?t=2272475&p=13259948#post13259948](http://ubuntuforums.org/showthread.php?t=2272475&p=13259948#post13259948)

**SOLUTION:**

step 1: go to [http://mirrors.kernel.org/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.2+14.04.20140402-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libindicator/libindicator7_12.10.2+14.04.20140402-0ubuntu1_i386.deb)

step 2: download the libindicator7_12.10.2+14.04.20140402-0ubuntu1_i386.deb file.

step 3: go to [http://mirrors.kernel.org/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.1+13.10.20130920-0ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/liba/libappindicator/libappindicator1_12.10.1+13.10.20130920-0ubuntu4_i386.deb)

step 4: download the libappindicator1_12.10.1+13.10.20130920-0ubuntu4_i386.deb file.

step 5: go to [https://www.google.com/chrome/browser/desktop/index.html?system=true&standalone=1](https://www.google.com/chrome/browser/desktop/index.html?system=true&standalone=1)

step 6: the page, will look like **[THIS]("http://i.imgur.com/p8dhGAS.jpg"), **left click the "Download Chrome for another platform" text.

step 7: a new menu will appear like [**THIS,**]("http://i.imgur.com/v13iKzK.jpg") left click the blue "Linux" text.

step 8: a new menu will appear like **[THIS,]("http://i.imgur.com/hWPQO8T.jpg") **left click the "32 bit .deb (for debian/ubuntu). And then left click the "Accept and install" button.

step 9: wait for all of the downloads to finish. When all downloads are finished, copy all of the [**THREE FILES**]("http://i.imgur.com/G63PaX6.jpg") to the flash drive.

step 10: Plug in the flash drive to the ubuntu computer, and copy all files to the home folder.

step 11: Pres "CTRL" "ALT" "T" button on the keyboard to open terminal.

step 12: type in "sudo dpkg -i libindicator7_12.10.2+14.04.20140402-0ubuntu1_i386.deb" and then pres "enter". And then, if the terminal ask for password, type in the password, and then press [enter]. [**LIKE THIS.**]("http://i.imgur.com/qcVYBkP.jpg")

step 13: wait for the terminal to finish the process. When the terminal waits for your input, then the process is finished.

step 14: type in: "sudo apt-get install libappindicator1" and then press [enter]. And then, if the terminal ask for password, type in the password, and then press [enter]. [**LIKE THIS.**]("http://i.imgur.com/k0R10Ax.jpg")

step 15: The terminal will ask you "do you want to continue? [Y/n]" . Type in "y" and then press [enter].

step 16: Wait for the terminal to finish the process [**LIKE THIS**]("http://i.imgur.com/RefZC0G.jpg"). And then, google chrome should already be installed on your ubuntu computer.

to run the google chrome program: open terminal, and then type in: "google-chrome-stable". And then press enter.

To completely remove and uninstall google chrome:

step 1: open terminal, then type in: "sudo apt-get purge google-chrome-stable". And then press enter.

step 2: Still in the terminal, type in: "rm ~/.config/google-chrome/ -rf". And then press enter.

To install google chrome again after uninstalling:

step 1: Type in: "sudo dpkg -i google-chrome-stable_current_i386.deb". And then press enter.

step 2 : Type in your super user password, and then press enter.

---

### Post by Adam_GUI on 2015-04-10
"sudo dpkg -i google-chrome-stable_current_i386.deb"

---

### Post by newbie14 on 2015-04-10
Thank you Adam_GUI but after executing the command,
 [ATTACH=CONFIG]261215[/ATTACH]
the terminal replied that it encountered an error.
I still want to install google chrome.
What should I type now?

---

### Post by Adam_GUI on 2015-04-10
Urk...
You're missing a dependency.
You need "libappindicator1".

Apt or dpkg could have looked for any dependencies if you had a connection.
I know that's not exactly helpful...

Here's the Ubuntu page for that package:
[http://packages.ubuntu.com/trusty/libappindicator1]("http://packages.ubuntu.com/trusty/libappindicator1")
Please be sure that you're running Trusty. (14.04)

You can try downloading the correct deb file for your architecture to your pen drive and try installing in the same manner.

Edit:
If your dependency has further dependencies (What got dubbed Dependency Hell in the Fedora/Fedora Core days),
you could run into the same problem again.

---

### Post by newbie14 on 2015-04-11
I am certain that my Ubuntu is version 14.04.
But I am not sure about Trusty.
What to type in the terminal to check whether or not my ubuntu computer is running Trusty?
meanwhile, I will check your hyperlink.

---

### Post by Bashing-om on 2015-04-11
newbie14; Hello:

> **newbie14 said:**
> I am certain that my Ubuntu is version 14.04.
But I am not sure about Trusty.
What to type in the terminal to check whether or not my ubuntu computer is running Trusty?
meanwhile, I will check your hyperlink.

The terminal command:
```

lsb_release -a

``` will do that for ya.

[INDENT][INDENT][INDENT]all here to help
[/INDENT][/INDENT][/INDENT]

---

### Post by newbie14 on 2015-04-11
> **Bashing-om said:**
> will do that for ya.
[INDENT][INDENT][INDENT]all here to help
[/INDENT]
[/INDENT]
[/INDENT]


Thank You Bashing-om, now I know the codename of my ubuntu version.

---

### Post by newbie14 on 2015-04-11
> **Adam_GUI said:**
> Please be sure that you're running Trusty. (14.04)

Confirmed,
in this image: [http://i.imgur.com/FhYuUvc.jpg](http://i.imgur.com/FhYuUvc.jpg) The terminal replies at the fifth line with the codename of my ubuntu version.
Apparently, I am running Trusty.

---

### Post by newbie14 on 2015-04-12
I went to this hyperlink:
[http://packages.ubuntu.com/trusty/libappindicator1]("https://help.ubuntu.com/community/PopularPages")
I right clicked the option that said i386.
I left clicked the open in new tab option.
[like this.]("http://i.imgur.com/LDkiEKh.jpg")
I downloaded the first hyperlink the web page provided.
[like this.]("http://i.imgur.com/oLLwZvA.jpg")
The libappindicator1 had been downloaded.
[like this.]("http://i.imgur.com/RfCXWe7.png")
I copied the libappindicator1.deb to the flash drive, bring it home, and tried to install it.
The terminal replies that I need to install libappindicator7 first.
[like this.]("http://i.imgur.com/gPEHdc2.jpg")
I will be right back while I search for this libappindicator7.

---

### Post by Bucky Ball on 2015-04-12
> **newbie14 said:**
> I went to this hyperlink:
[https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages)
I right clicked the option that said i386.
I left clicked the open in new tab option.
[like this.]("http://i.imgur.com/LDkiEKh.jpg")
I downloaded the first hyperlink the web page provided.
[like this.]("http://i.imgur.com/oLLwZvA.jpg")
The libappindicator1 had been downloaded.
[like this.]("http://i.imgur.com/RfCXWe7.png")
I copied the libappindicator1.deb to the flash drive, bring it home, and tried to install it.
The terminal replies that I need to install libappindicator7 first.
[like this.]("http://i.imgur.com/gPEHdc2.jpg")
I will be right back while I search for this libappindicator7.

You are now entering what was previously described as 'dependency hell' and it can be like finding a needle in a haystack. With any luck, though, libappindicator7 will not require further missing dependencies ...

---

### Post by coffeecat on 2015-04-12
I have to ask because I'm curious. Perhaps I'm missing something.

Why would you want to install a web-browser in an offline computer? If it's going to stay offline, then I can't see any point in installing Google Chrome. If you're going to put in online in due course, why not do so in order to install Google Chrome? Then the deb package you have will download the dependencies it needs automatically.

---

### Post by newbie14 on 2015-04-12
Because there is this particular animated .gif picture file that can only appear properly using google chrome application. It cannot be viewed with other program, not mozilla firefox, not faststone image viewer, not Adobe Photosop, not even ACDSee. If this file is opened with programs other than google chrome, the picture's (possessive, picture's? picture'? pictures'?) color is blinking randomly and some color turn to black or white, other programs doesn't animate the picture, total mess. The main purpose of this google chrome is to view an animated .gif file.

---

### Post by newbie14 on 2015-04-12
> **Bucky Ball said:**
> libappindicator7 will not ...

Where is this libappindicator7 located at? where can I find it? at what u.r.l address should I go to download this libappindicator7 using windows computer?

wait, I found it at
[http://packages.ubuntu.com/trusty/libs/libindicator7](http://packages.ubuntu.com/trusty/libs/libindicator7)
and
[http://packages.ubuntu.com/trusty/i386/libindicator7/download](http://packages.ubuntu.com/trusty/i386/libindicator7/download)

I will try something...

---

### Post by newbie14 on 2015-04-12
And oh, I want to make a complete tutorial on how to install google chrome on offline computer, with ubuntu installed on flash drive, and the computer uses i5 processor, and the ubuntu version is 14.04 codenamed Trusty.

---

### Post by Bashing-om on 2015-04-12
newbie14; Hey hey ...

You do good work ! We are interested in your little project, let us know how it goes.

I do not wish you luck, as I know it is time. effort and study that counts here.

[INDENT][INDENT][INDENT]the good thing is
[INDENT][INDENT][INDENT][INDENT]it is do-able
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by newbie14 on 2015-04-12
so I have downloaded the libindicator7 .deb file successfully
[like this.]("http://i.imgur.com/hrIh4fK.jpg")
And I copied that file to the flash drive and then copied it to my home folder in my ubuntu computer.
And then I opened the terminal.
And then I typed
sudo dpkg -i libindicator7_12.10.2+14.04.20140402-0ubuntu1_i386.deb
And then the terminal replies with some lines of processes,
the last line the terminal replied is "processing triggers for libc-bin (2.19-0ubuntu1) ...
And then the terminal stands by, waiting for my input.
[like this.]("http://i.imgur.com/2QYfhmw.jpg")
My questions are:
1. Is that libindicator7 package has been successfully installed?
2. What should I type in the terminal to figure out whether libindicator7 has been successfully installed or not?

---

### Post by Bashing-om on 2015-04-12
newbie14; Yep;

So far so good:
As you returned to prompt from the install command - and no errors, the system did as told.
You can verify:
```

dpkg -l libindicator7

```
the response should be:
> 
sysop@1404mini:~$ dpkg -l libindicator7
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libindicator7  12.10.2+14.0 amd64        panel indicator applet - shared l
sysop@1404mini:~$

where the " ii  libindicator7  " -> ii is "(i)nstalled (desired) and (i)nstalled (status) .

So now is the package manager in a happy state ?
```

sudo apt-get -f install
sudo dpkg -C

```

[INDENT][INDENT]wishing all is well
[/INDENT][/INDENT]

---

### Post by newbie14 on 2015-04-12
I am glad to hear that. But before I type any codes I don't understand yet in the terminal, I have 2 questions:
1. What will "sudo apt-get -f install" do?
2. What will "sudo dpkg -C" do?

---

### Post by Bashing-om on 2015-04-12
newbie14; Yeah !

Always a wise thing to understand what the commands are, and the why-for-thou .
"apt-get -f" is (F)ix missing;
"dpkg -C" is audit the system for broken packages.

the full story:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by newbie14 on 2015-04-13
Hey, It works, haha. Thaks a lot Adam_GUI, Bashing-om.

---

### Post by Bashing-om on 2015-04-13
newbie14; Outstanding !

> **newbie14 said:**
> Hey, It works, haha

You do good work:

If this matter is now concluded, and you are satisfied with 'your' result:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

we move on to the next adventure
[INDENT][INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-04-13
Totally off-topic, but just to clear something up for you ...

pictures' = it belongs to lots of pictures. Picture's = it belongs to one picture. The s' is for collective possession, the 's is for singular.

The mayor's hat blew off = one particular mayor's hat blew off. The mayors' hats blew off = all of the 25 mayors' hats blew off. The cat's stench = one cat's stench. The cats' stench = all of these particular thirteen cats stench (but not ALL cats)! ;)


Glad you got your Chrome issue sorted.

---

### Post by newbie14 on 2015-04-13
Noted.

However I have some more questions.
Now that I have installed google chrome, it doesn't appear in "installed" tab in the "ubuntu software center". Even in the "uncategorized" subfolder tree. Even typing "chrome" in the search box in the "ubuntu software center" doesn't reveal the google chrome program. My question is:
1. What should I type in the terminal to check whether google chrome has already been installed or not?
2. What should I type in the terminal to launch the google chrome program?
3. What should I type in the terminal to completely uninstall google chrome program?

---

### Post by slickymaster on 2015-04-13
> **newbie14 said:**
> Noted.

However I have some more questions.
Now that I have installed google chrome, it doesn't appear in "installed" tab in the "ubuntu software center". Even in the "uncategorized" subfolder tree. Even typing "chrome" in the search box in the "ubuntu software center" doesn't reveal the google chrome program. My question is:
1. What should I type in the terminal to check whether google chrome has already been installed or not?
2. What should I type in the terminal to launch the google chrome program?
```
google-chrome-stable
```
> **newbie14 said:**
> What should I type in the terminal to completely uninstall google chrome program?
```
sudo apt-get purge google-chrome-stable
rm ~/.config/google-chrome/ -rf
```

---

