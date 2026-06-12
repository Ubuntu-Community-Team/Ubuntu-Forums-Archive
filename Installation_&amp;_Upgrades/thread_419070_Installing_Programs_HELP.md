---
title: "Installing Programs HELP"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by djnick101 on 2007-04-22
Hi All,
I'm new to Linux and have dual boot with Windows XP on my home system.

My son, who's a "geek"(a loving term) got me interested in Linux so I thought I'd give it a try.

My problem is trying to find and install programs after I've downloaded them. With Windows you just save them into a folder and then double click on the installer and bingo it installs.

I've downloaded a couple of programs but I don't know where they went or how to find them. I'm not even sure what kind of extension they have.

I'm not sure but I have at least two things going against me. I'm 61 and Polish so please be kind and only throw soft things.:lolflag: 

Thanks for any help you can give
Dale

---

### Post by raja on 2007-04-22
Where did you download the programs from? Most programs you need will be in the ubuntu repositories. So when you want any program, use Synaptic package manager, search for it, select what you want and click install. The program will be downloaded automatically, installed and added to the programs menu. 
If you tell me what exactly you were installing I can offer more specific help.

---

### Post by djnick101 on 2007-04-22
Hi raja,

I just installed Thunderbird email program. The Synaptic installer said it downloaded and installed but I can't find it with any of the icons at the top of the page.

Dale

---

### Post by raja on 2007-04-22
Do you mean the panel at the top of the page? If you can see the program in the "Applications" menu, you can just drag the icon to the panel to put it there.

---

### Post by djnick101 on 2007-04-24
Hi again raja,

I do mean the Applications menu at the top left. But when I click it open there is no sign of Thunderbird anywhere in any of the icon groups. It isn't on my desktop either. If I do a search for it it comes up in a seperate window and I've tried clicking every catagory but don't get anything that looks like a program. And, nothing runs either.

---

### Post by raja on 2007-04-24
I would check if the program was installed properly by typing ```
thunderbird
```in the terminal. You can also try this by pressing Alt-F2 which will bring up a launcher in which you can type this. If any of this launches the program, you know it is there and working. In that case, you can use ```
alacarte 
``` to add the application to the menu manually.

---

### Post by djnick101 on 2007-04-25
OK. I tried that but it said, "Could not open location 'file:///Thunderbird' and The location or file could not be found."

When I find "Thunderbird" with the Synaptic Package Manager and right click it a window pops up asking me whether I want to reinstall it or remove it or mark it for complete removal.

If I'm reading it right it's already installed on the computer but my problem is finding it and getting an icon or something so I can use it. I've tried double-clicking everything that comes up for Thunderbird but don't get anything to run. With Windows XP it asks you what folder you want it in so you can find it again and install it. Here it just says it's installed but doesn't tell you where to go to use it and run it.

That's my main problem. How do I find it and use it. Or at least put an icon somewhere where I know where it is so I can use the program I download.

I'm Polish, what can I say? :lolflag:

---

### Post by raja on 2007-04-25
Did you try it with as 'thunderbird' with a small t? The name will be case-sensitive.
The main executable file will be installed in /usr/bin. You can find out by trying ```
whereis thunderbird
``` But you dont really need to do that. if you are really having problems still, try to reinstall it through synaptic.

---

### Post by chrisfisehr on 2007-04-25
I just installed Ubuntu over Windows XP over the weekend.  It really sped up both start up and shut down on my 1.0Ghz laptop, gave me longer batter life (can't figure that one out), and fixed a wireless card issue (that I always attributed to a bios problem)...who would of thought?  Nevertheless, the file structure of Ubuntu is driving me crazy. It seems so unintuitive. I've tried installing some programs myself, and they go into never-never land or refuse to install altogether.  I just tried installing R (a statistical package) listed in Synaptic. It too has gone into the abyss with no record of it. My questions is, will Synaptic create a shortcut in the Applications menu for everything I install? If so, it didn't with R.  I have to say that the file system and applications, in general, is frustrating. I am going to stick with Ubuntu for a week or two and see how it goes...  Thanks!!

---

### Post by raja on 2007-04-26
Hello Chris,
Welcome to Ubuntu. You must accept that you will have some difficulties in the beginning and must not get discouraged.
The file-system is not really weird or unintuitive - it is just very different from windows, I am sure you will appreciate some advantages as time goes on.
Not everything that you install will show up in the menu. It is a problem at present. I rarely use the menu and have never found this an issue though. However, a solution is to install the debian menu which will show all applications. You can look at [this page]("http://ubuntuforums.org/showthread.php?t=416134") on doing this in Feisty. 
For R, I dont even see the point of a menu entry. You will be using it with an editor or from the terminal. To use R, I just open the terminal and type 'R'. That should get you started.

---

### Post by chrisfisehr on 2007-04-26
Thanks for the kind welcoming.  I will check out the debian menu.  I tried the R in the terminal, and it said the software was not installed. Synaptic says it is. I guess it was a bad install. I'll uninstall/reinstall.  Is there a shortcut command for the terminal? If all I have to do to launch an application is type the name in the terminal, than that it is cool.  I use Launchy in XP, which is a text command launcher.  I just don't want to have to write code.. I simply don't have time to learn linux code.  thanks again for you help!

---

### Post by raja on 2007-04-27
You can launch applications from the terminal. If you have the terminal open all the time (like me), that is easy. However, the equivalent to launchy is Alt-F2 in gnome or Alt-Space in KDE will bring up a launcher - try it out.

---

### Post by djnick101 on 2007-04-28
Hi raja,

I think I have it figured out. I actually got Thunderbird installed and working. I feel like a kid who got his first car.:lolflag: 

I ordered and received(today) a Dummies book on ubuntu. It seemed to help, at least I have my first program downloaded and installed.

Now to try it again just to make sure it wasn't a fluke.

Thanks for your help. It's appreciated.

Dale

---

