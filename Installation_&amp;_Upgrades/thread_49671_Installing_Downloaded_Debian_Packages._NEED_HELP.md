---
title: "Installing Downloaded Debian Packages. NEED HELP"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by Kimothy on 2005-07-17
Hi. Im going to install java. I downloaded the newest .rpm package and used alien to turn it into debian. How to you install these kind of debian packages?

I would belive it would be like this in my case...

root@bebe:/home/kim/Downloads/Bittorrent # dpkg -i [jre_1.5.0_04-1_i386.deb]

... but it doesent work. I NEED HELP

How to you install packages you have downloaded? I know I probobly can install java from synaptic, but thats not the point...

Thanks for any reply I might get

---

### Post by dave9191 on 2005-07-17
If you want java you can get it from synaptic, or download it from the sun java website (that comes with a scripts that installs it for you). But if you are keen to do it from a converted rpm (remember thats its still experimental) you are on the right lines. 

Without giving the error output of dpkg I can only guess that its complaining about not having permission to write to disk, it has to be run as root. So put sudo before the dpkg command. 

sudo dpkg -i jre_1.5.0_04-1_i386.deb

Dave

---

### Post by Kimothy on 2005-07-17
Thanks for the reply, but I did run the command as su (not as sudo, su). So that can't be the case...

---

### Post by dave9191 on 2005-07-17
Oh, i didnt notice that you were root, sry. But like I said, without the error message its hard to help. 

Dave

---

### Post by Kimothy on 2005-07-17
[QUOTE=Kimothy]Thanks for the reply, but I did run the command as su (not as sudo, su). So that can't be the case...[/QUOTE]

I'm quoeting my self no... I loged in as sudo in the terminal and i typed sudo before the dpkg command. What to you make of this? It's not installed, is it?

root@bebe:/home/kim/Downloads/Bittorrent # sudo dpkg -i jre_1.5.0_04-1_i386.deb
(Reading database ... 68648 files and directories currently installed.)
Preparing to replace jre 1.5.0_04-1 (using jre_1.5.0_04-1_i386.deb) ...
Unpacking replacement jre ...
Setting up jre (1.5.0_04-1) ...
root@bebe:/home/kim/Downloads/Bittorrent #

---

### Post by dave9191 on 2005-07-17
Well its not complaining about anything, and its says that it was replacing so it must have intalled before. It should be there now. Try typing java and see if that outputs something or says command not found. 

If it says command not found, then it might not be in your path, so do a 

sudo updatedb
locate java

Dave

---

### Post by Kimothy on 2005-07-17
[QUOTE=dave9191]Well its not complaining about anything, and its says that it was replacing so it must have intalled before. It should be there now. Try typing java and see if that outputs something or says command not found. 

If it says command not found, then it might not be in your path, so do a 

sudo updatedb
locate java

Dave[/QUOTE]

I found a lot of java with the 'locate java' command, typing java in the terminal resulted in command not found.

The reason why I need java is run azureus... but I cant install java untill i have java 1.4++ installed. I was thinking that becouse the java package I installed was original a .rpm package, that the version number was not updated (that's realy commen...) and so then azureus has no way of knowing i have java 1.5.

Thanks for the reply

---

### Post by dave9191 on 2005-07-17
Im going to take a guess and say that the rpm package has installed java into a non standard location and therefore its not in you path. You need to find the java executable and add that to your path. 

try  

locate java | grep bin 

to minimise the number of results. find the location of that java bin file (..../bin/java) and add that to you path. You might want to look that up if you dont know how to add something to your path. 

I think its 

export $PATH:/..../bin/

But I could be wrong. Of course replace the /.../bin/ with the location of java's folder. And if 'java' works after that, you might want to add it to your .bashrc file so that it does this for you auatomatically. 

Dave

---

### Post by eMuNiX on 2005-07-17
[QUOTE=Kimothy]I found a lot of java with the 'locate java' command, typing java in the terminal resulted in command not found.

The reason why I need java is run azureus... but I cant install java untill i have java 1.4++ installed. I was thinking that becouse the java package I installed was original a .rpm package, that the version number was not updated (that's realy commen...) and so then azureus has no way of knowing i have java 1.5.

Thanks for the reply[/QUOTE]

I have just installed azureus using 'sudo apt-get install azureus' the java is installed as a dependency at this stage, it gets these from the backport locations in your sources.list it should also install a number of other dependencies at the same time.

---

### Post by Kimothy on 2005-07-17
I found java here:

/usr/java/jre1.5.0_04

but no executeble.

I checked synaptic and i seems that java runtime eviroment 1.5 is installed... I can't understand why azureus dont see that...

---

### Post by Kimothy on 2005-07-17
shouldent azureus be availeble in synaptic? Do you know of any good reposotories i can try out?

by the way...

kim@bebe:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package azureus
kim@bebe:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

this is not good is it?

---

### Post by dave9191 on 2005-07-17
Id say that you have apt-get or synaptic or something similar already running. If it cant access the lock file, it means something else already has it locked, or you arent root (which you are in this case). 

If you find the java bin file, you should be able to run it. It says it needs java 1.5 on the website and both of these are avaible in the repositories 

sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)

So I dont really know why you are fighting with an rpm file. If you really dislike the repositories then you could have gotten whatever version you wanted from the sun site. 

Dave

---

### Post by Kimothy on 2005-07-17
Your right. Java is fine, but azureus will not install. It says i don't have Java and so It tells me to install it. This is the problem... I thought java was not installed, couse I was told so when i tried to install azureus. So i tried to install it with the package you can download from the azureus homepage... but I don't need do do this becouse Java IS insalled, but I cant install Java becouse Java 'is not' installed.

Thanks for all the replys

---

### Post by dave9191 on 2005-07-17
So azureus comes with an installationg program? I would have imagined that it just comes wtih a jar file that you need to run using java. 

Something like 

java -jar Azuresu.jar 

Or whatever the file is called. 

Dave

---

### Post by Kimothy on 2005-07-17
Azureus dosent come with an installer in the same sense as a windows application, but as './azureus' command in the terminal... A .sh file

---

### Post by dave9191 on 2005-07-17
In that case the shell script probably doesnt know where your java file is. Open it in a text editor and edit where its looking for the java bin file. 

Dave

---

