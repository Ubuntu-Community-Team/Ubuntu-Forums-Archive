---
title: "dpkg --config -a error after failed install"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by illuminaris on 2007-09-27
I'm new to Ubuntu/Linux and these forums, so I apologize if I do a poor job of asking for help, but I am in quite a predicament here.

I was trying to install multi-media codecs using the code:
sudo apt-get install ubuntu-restricted-extras
Everything was going great until a terms of service agreement came up in my terminal. There was no option for input, just a bunch of text and no cursor. I tried a bunch of different buttons, ENTER, Y, N, SPACE, whatever. Finally I gave up and couldn't figure out how to agree to the terms of service, so I closed out of the terminal assuming I would just have to remove the portion of the program that had already downloaded or something along those lines. To my unpleasant surprise, the next time I tried to install something through the terminal I got this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I tried going into my synaptic manager instead, and the same error appeared.
I attempted to input the 'dpkg --configure -a' command in my terminal and got this feedback:
dpkg: requested operation requires superuser priviledge

So now I can't install anything through my terminal or my synaptic manager and I am a little worried/frustrated. Can someone please give me a step-by-step in simple terms on how to solve this problem? Thanks in advance for all your help!

---

### Post by forestpixie on 2007-09-27
you need to use sudo

```
sudo dpkg --configure -a
```

---

### Post by illuminaris on 2007-09-27
Ok, thanks, that got me one step further. Now, when I used that command it gives me this feedback.

"dpkg: error processing -a (--configure):
no package named `a' is installed, cannot configure
Errors were encountered while processing:
a"

So I tried replacing -a with the name of the file package I downloaded and the same error comes up. Any ideas?

Also, does anyone know how you are supposed to accept Terms Of Service agreements when there is no input cursor, in case that happens again?

---

### Post by rsambuca on 2007-09-27
> **illuminaris said:**
> Ok, thanks, that got me one step further. Now, when I used that command it gives me this feedback.

"dpkg: error processing -a (--configure):
no package named `a' is installed, cannot configure
Errors were encountered while processing:
a"

So I tried replacing -a with the name of the file package I downloaded and the same error comes up. Any ideas?

Also, does anyone know how you are supposed to accept Terms Of Service agreements when there is no input cursor, in case that happens again?
Use the arrow keys to move through the java terms.

as for the firs part, copy and paste the following into a terminal.  Do not type it, just copy and paste it:```
sudo dpkg --configure -a
```

---

### Post by illuminaris on 2007-09-27
For some reason it allows me into my synaptic manager now, which is very good news! Thanks for all your help so far.

The new problem is this, when I go into my synaptic manager it tells me I have one broken file. When I go to my broken filter it lists this file:
sun-java6-bin

That is, of course, what I tried to install. But when I try to mark it for removal and remove it, an error occurs. It says:

E: sun-java6-bin: Package is in a very bad inconsistent state - you should

and then it cuts off and doesn't finish the statement.

Any ideas on how to fix this problem? Sorry for being so complicated.

As for the Terms Of Service window that originally came up in my terminal, I did use the arrow keys to scroll, the problem was that I couldn't agree to it. I scrolled to the bottom, to the top, back to the bottom, it wasn't doing anything. How do I agree, is there an F key or something like that? Nothing was listed.

---

### Post by rsambuca on 2007-09-27
> **illuminaris said:**
> For some reason it allows me into my synaptic manager now, which is very good news! Thanks for all your help so far.

The new problem is this, when I go into my synaptic manager it tells me I have one broken file. When I go to my broken filter it lists this file:
sun-java6-bin

That is, of course, what I tried to install. But when I try to mark it for removal and remove it, an error occurs. It says:

E: sun-java6-bin: Package is in a very bad inconsistent state - you should

and then it cuts off and doesn't finish the statement.

Any ideas on how to fix this problem? Sorry for being so complicated.

As for the Terms Of Service window that originally came up in my terminal, I did use the arrow keys to scroll, the problem was that I couldn't agree to it. I scrolled to the bottom, to the top, back to the bottom, it wasn't doing anything. How do I agree, is there an F key or something like that? Nothing was listed.
Perhaps it was the tab key.  I don't recall offhand.

Try opening a terminal and ```
sudo apt-get --purge sun-java6-bin
```

---

### Post by illuminaris on 2007-09-27
Dang, I tried your command and it gave me this error:

E: Invalid operation sun-java6-bin

That, in my opinion, obviously means such a file doesn't exist, yet that specific file shows up in my synaptic manager as "broken", so how does that make sense.

I tried TAB in the Terms Of Service screen originally, but it didn't work. I had tried TAB, CAPS LOCK, SPACE, ENTER, Y, and N. None of them worked.

---

### Post by rsambuca on 2007-09-27
I think I just have the wrong command.  Try 

sudo apt-get remove sun-java6-bin

---

### Post by forestpixie on 2007-09-27
I think it needs to be 

```
sudo apt-get remove --purge sun-java6-bin
```

> I tried TAB in the Terms Of Service screen originally, but it didn't work. I had tried TAB, CAPS LOCK, SPACE, ENTER, Y, and N. None of them worked.

I thought space got to the end of the agreement and then it might have a > type yes to agree at the end

---

### Post by illuminaris on 2007-09-27
I tried your new command and it worked, a bunch of junk scrolled in the terminal, then at the end it gave me the same error it was giving me in the synaptic manager, except this time it finished the sentence. 

dpkg: error processing sun-java6-bin (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.

E: Sub-process /usr/bin/dpkg return an error code (1)

So, can I just re-install it through synaptic manager? Should I re-do the same code I originally used to install it through the terminal? Do I have to install something different, like a base Java?

No, there was no "yes to continue" or anything like that. It was just the text from the Terms Of Service and nothing else. No continue command, nowhere you can type.

---

### Post by forestpixie on 2007-09-27
you could try to re-install through synaptic or through terminal

```
sudo aptitude reinstall sun-java6-bin
```

if you still get a problem see what this gives you

```
sudo  dpkg -C
```

I've never used it - didn't learn where the manuals were until the major problem I'd got had been solved - so never used it in anger :) Supposedly it will suggest what to do with a problem - if it says something like  reinst-required

try this to get rid

```
sudo dpkg --remove --force-remove-reinstreq sun-java6-bin
```

---

### Post by illuminaris on 2007-09-27
The problem was fixed by downloading Automatix2, which replaced Java and also explained to me that the "restricted" codecs are called Non-Free codecs. They are actually illegal to download in America, so be careful and download at your own risk. I had no idea what I was even downloading, I guess that's one of the scarier aspects of using Linux as a newbie. Heh. Anyways, thanks for all your help and problem solved.

---

### Post by hlp on 2007-10-02
i'm using ubuntu 7.04 Yesterday I try this code
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager

```
 then my terminal like this
[IMG]http://i219.photobucket.com/albums/cc30/hlpdt10/Screenshot.png[/IMG]
I close my terminal....so then when i try to install w32codes by code
```

sudo apt-get install w32codecs

```
 my terminal say that i have to try 
```

sudo dpkg --configure -a

```

i retry to install w32codecs but i'm not success....i try to remove sun-java6-bin but don't work...


sbd help me...plz:(

---

### Post by rsambuca on 2007-10-02
The problem is you closed your terminal without agreeing to the java agreement.

Open a terminal and run the command that it told you:```
sudo dpkg --configure -a
```

---

### Post by hlp on 2007-10-02
yes..but i can't see the agreement .....i drag to an end of liscense but there isn't agree ment...as you can see like this:
[IMG]http://i219.photobucket.com/albums/cc30/hlpdt10/Screenshot-1.png[/IMG]

there is no agreement

when i try 
```

sudo dpkg --configure -a

```
there is nothing happen..then i try 
```

sudo apt-get install w32codecs

```
my terminal show this
```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-00-2ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-00-2ubuntu2) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

then i try 
```

sudo apt-get  -f install

```
my terminal
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho
Recommended packages:
  gsfonts-x11
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/32.5MB of archives.
After unpacking 93.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```
i type y
then my terminal show the the picture as above.....but i can't see the agree ment.....plx help me....
you can contact me by yahoomessenger...my nick is 
pdhlnpt


thank you for your help......

---

### Post by rsambuca on 2007-10-02
Press tab and highlight the "OK", and then press enter!

---

### Post by hlp on 2007-10-02
thank you...now  i can see the lisence....now i'm trying to install...thank you for all....


OK.....

---

