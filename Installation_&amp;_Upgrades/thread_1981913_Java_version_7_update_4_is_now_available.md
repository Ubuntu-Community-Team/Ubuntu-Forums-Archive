---
title: "Java version 7 update 4 is now available"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2012-05-17
It is recommended that you update Java to version 7 for security reasons.
Do not download the .RPM versions as they are for other distros.

Click on the Linux version if you have a 32 bit machine and the Linux x64 version if you have a 64 bit machine. 
Download the file to your Downloads directory and [COLOR=Red]do not use Archive Manager[/COLOR].

The file ends in .tar.gz  The instructions in the green link are pretty self explanatory. 
The 32 bit instructions are on the left and the 64 bit instructions are on the right.

Where it says GET JRE ([COLOR=Green]in the green link[/COLOR]) is where you can download the latest version to install.
You can actually get the download from either link.

It says to remove the old version first with a link to take you to the bottom where those instructions are.
Then go back up and start installing. It's just a matter of copying and pasting.

---

### Post by samwillc on 2012-05-17
Hi,

Maybe I'm being a bit daft here but I can't install it. I have created /usr/java/

Downloaded jre-7u4-linux-x64.tar.gz, extracted that to Downloads so I have a folder called jre-7u4-linux-x64.

How do I make this into a .bin file??

The instructions on the java website are as follows:
** Linux self-extracting**

 Follow these instructions: 
[LIST=1]
[*]**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-7u<version>-linux-i586.bin
where <version> is to be replaced by the version downloaded. 
**Example**: For jre-7u3, the command is 
chmod a+x jre-7u3-linux-i586.bin
[/LIST]

Firstly, what file? I have extracted a folder... So I get the following in terminal:

sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.bin
[sudo] password for sam: 
chmod: cannot access `jre-7u4-linux-x64.bin': No such file or directory

I can't see what I'm doing wrong? Did I even have to extract first?

Also tried this:

sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.bin
chmod: cannot access `jre-7u4-linux-i586.bin': No such file or directory

Not going too well this!

Any help is much appreciated as always, thanks.

Sam.

---

### Post by sammiev on 2012-05-17
Hope this helps you as I took [this]("http://ubuntuforums.org/showthread.php?t=1977358") update sometime a go.

---

### Post by samwillc on 2012-05-17
Brilliant thanks. Still not sure why the instructions above didn't work for me, but you've certainly speeded the process up!

[IMG]http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-05-17%2021%3A42%3A07.png[/IMG]
Thanks again.

Sam.

---

### Post by Cavsfan on 2012-05-17
> **Cavsfan said:**
> Download the file to your Downloads directory and [COLOR=Red]do not use Archive Manager[/COLOR].

The file ends in .tar.gz 

> **samwillc said:**
> Hi,

Maybe I'm being a bit daft here but I can't install it. I have created /usr/java/

Downloaded jre-7u4-linux-x64.tar.gz, extracted that to Downloads so I have a folder called jre-7u4-linux-x64.

How do I make this into a .bin file??

The instructions on the java website are as follows:
** Linux self-extracting**

 Follow these instructions: 
[LIST=1]
[*]**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-7u<version>-linux-i586.bin
where <version> is to be replaced by the version downloaded. 
**Example**: For jre-7u3, the command is 
chmod a+x jre-7u3-linux-i586.bin
[/LIST]

Firstly, what file? I have extracted a folder... So I get the following in terminal:

sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.bin
[sudo] password for sam: 
chmod: cannot access `jre-7u4-linux-x64.bin': No such file or directory

I can't see what I'm doing wrong? Did I even have to extract first?

Also tried this:

sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.bin
chmod: cannot access `jre-7u4-linux-i586.bin': No such file or directory

Not going too well this!

Any help is much appreciated as always, thanks.

Sam.

You used Archive Manager. Just download the file again and select "save file".
Then go back to where you left off.

---

### Post by Cavsfan on 2012-05-17
> **sammiev said:**
> Hope this helps you as I took [this]("http://ubuntuforums.org/showthread.php?t=1977358") update sometime a go.

My link to check versions kept telling me that my version 6.32 was the correct version. Not sure what to make of that.

But, these instructions work. QIII and I were on another thread where I found out 7.4 was the most current.

I know about the ppa and all. I just prefer to do this the manual way. I usually am up to date a lot quicker than the ppa.
With the exception of this time. :shock:

---

### Post by Cavsfan on 2012-05-17
> **samwillc said:**
> Brilliant thanks. Still not sure why the instructions above didn't work for me, but you've certainly speeded the process up!

[IMG]http://dl.dropbox.com/u/63070476/Screenshot%20from%202012-05-17%2021%3A42%3A07.png[/IMG]
Thanks again.

Sam.

Glad you got it sorted out. See my prior reply for the reason why it didn't go so smooth for you.
With Ubuntu there is a constant need to learn. I learn stuff all the time.
Cheers

---

### Post by Cavsfan on 2012-05-17
> **samwillc said:**
> Downloaded jre-7u4-linux-x64.tar.gz.
chmod a+x jre-7u<version>-linux-i586.bin

Do you have a 32 bit machine or a 64 bit machine?
32 bit file name >> jre-7u4-linux-i586.tar.gz
64 bit file name >> jre-7u4-linux-x64.tar.gz

It's OK to install the 32 bit Java on a 64 bit machine but, I recommend 64 bit Java for a 64 bit machine.

You mention both files here. I am confused.

BTW, these instructions can be performed over and over without any harm.

Those instructions do not mention .bin files just .tar.gz files??

---

### Post by samwillc on 2012-05-17
**sorry, I will clarify, I tried i586 purely because that was in the instructions. I have 64-bit. It was a long shot and I was trying any combinations I could think of.**

Hi, thanks for the help but I did just save in Downloads, then at terminal I tried the following combinations, no of which worked:

sam@sam-pc:~$ cd Downloads
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.bin
[sudo] password for sam: 
chmod: cannot access `jre-7u4-linux-i586.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.bin
chmod: cannot access `jre-7u4-linux-x64.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.tar.gz.bin
chmod: cannot access `jre-7u4-linux-x64.tar.gz.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.tar.gz.bin
chmod: cannot access `jre-7u4-linux-i586.tar.gz.bin': No such file or directory
sam@sam-pc:~/Downloads$ 

What is supposed to happen? Is the tar.gz supposed to turn into a .bin file? If so, it's not doing that.

Any other ideas why this is not working for me?

Sam.

---

### Post by Vereinfachen on 2012-05-17
Seriously, why do you guys go through the hassle to update it manually. Just wait until the ubuntu devs push the new version to the official repositorys and update it from there. Can't understand it ...

You know repositorys were invented for a reason.

---

### Post by samwillc on 2012-05-17
> **Cavsfan said:**
> Those instructions do not mention .bin files just .tar.gz files??

Wait a sec, what do you mean here? The instructions say write .bin on the end. I thought the tar.gz would 'turn into' a .bin.

Are these totally different things??

Sam.

---

### Post by samwillc on 2012-05-17
> **Vereinfachen said:**
> Seriously, why do you guys go through the hassle to update it manually. Just wait until the ubuntu devs push the new version to the official repositorys and update it from there. Can't understand it ...

Hi, it's because I am learning how. Speed is not essential to me, I am new to linux and think learning the basics would be a good idea.

Sam.

---

### Post by Cheesemill on 2012-05-17
Deleted[FONT=monospace][/FONT]

---

### Post by Cheesemill on 2012-05-17
> **Vereinfachen said:**
> Seriously, why do you guys go through the hassle to update it manually. Just wait until the ubuntu devs push the new version to the official repositorys and update it from there. Can't understand it ...

You know repositorys were invented for a reason.

Because Oracle Java isn't in the repositories anymore. It was removed due to legal reasons.

I don't do the manual update method either though, I use this PPA instead so that it updates automatically with the rest of my system.
[[FONT=monospace][FONT=Ubuntu]http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html[/FONT][/FONT]]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

---

### Post by samwillc on 2012-05-17
I think I was being a bit of a div, my new terminal command:

sam@sam-pc:~$ cd Downloads
sam@sam-pc:~/Downloads$ chmod a+x jre-7u4-linux-x64.tar.gz
sam@sam-pc:~/Downloads$ ls -l
total 33008
-rwxrwxr-x 1 sam sam 32881501 May 17 22:15 jre-7u4-linux-x64.tar.gz
sam@sam-pc:~/Downloads$ 

This seems correct. Why is there a .bin in the instructions? Is this for a different version of linux?

Sam.

---

### Post by Cavsfan on 2012-05-17
> **samwillc said:**
> **sorry, I will clarify, I tried i586 purely because that was in the instructions. I have 64-bit. It was a long shot and I was trying any combinations I could think of.**

Hi, thanks for the help but I did just save in Downloads, then at terminal I tried the following combinations, no of which worked:

sam@sam-pc:~$ cd Downloads
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.bin
[sudo] password for sam: 
chmod: cannot access `jre-7u4-linux-i586.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.bin
chmod: cannot access `jre-7u4-linux-x64.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-x64.tar.gz.bin
chmod: cannot access `jre-7u4-linux-x64.tar.gz.bin': No such file or directory
sam@sam-pc:~/Downloads$ sudo chmod a+x jre-7u4-linux-i586.tar.gz.bin
chmod: cannot access `jre-7u4-linux-i586.tar.gz.bin': No such file or directory
sam@sam-pc:~/Downloads$ 

What is supposed to happen? Is the tar.gz supposed to turn into a .bin file? If so, it's not doing that.

Any other ideas why this is not working for me?

Sam.

There is no mention of a .bin file in the instructions. I even searched for ".bin" and found nothing.
So, I don't know where you got that from.
Read my previous replies. I believe you used Archive Manager when you downloaded the file and you were supposed to choose "save file".

Those instructions are just a matter of copying and pasting. But, you have to read it carefully as it says to remove the old version first.
There is a link that will take you to the "remove instructions" or you can scroll down to them.
Then go back to the top and copy and paste, shut down FIrefox and open it back up.
Enter ```
about:plugins
``` in the url at the top and you should see:

**Java(TM) Plug-in 1.7.0_04**

 File:  /opt/java/64/jre1.7.0_04/lib/amd64/libnpjp2.so

If not try it again. Just go slow.

---

### Post by samwillc on 2012-05-17
Hi,

I can assure you I just saved the file, did not use archive manager,:

[http://javadl.sun.com/webapps/download/AutoDL?BundleId=63204](http://javadl.sun.com/webapps/download/AutoDL?BundleId=63204)

and followed the instructions here:

[http://java.com/en/download/help/linux_x64_install.xml](http://java.com/en/download/help/linux_x64_install.xml)

Clearly says under Install, point number 3:

**Change the permission of the file you downloaded to be executable**. Type: 
  chmod a+x jre-7u<version>-linux-i586**.bin**
where <version> is to be replaced by the version downloaded. 
**Example**: For jre-7u3, the command is 
chmod a+x jre-7u3-linux-i586**.bin**

This is why I thought I had to append .bin to the tar.gz file I had downloaded. I think all I had to do is use the actual filename of what I'd just downloaded:

i.e. sudo chmod a+x jre-7u4-linux-i586.tar.gz

I also downloaded the other versions (not to use) just to see if any of the files ended in .bin. They don't confusingly, so where did .bin come from in the instructions??

Does this make it clearer?

Sam.

---

### Post by Cavsfan on 2012-05-17
And I am in no way thinking you are slow! There is always something to learn about Linux and Ubuntu.
I don't think any one here knows everything there is to know!
I am still learning myself.

---

### Post by samwillc on 2012-05-17
> **Cavsfan said:**
> And I am in no way thinking you are slow!

Lol, don't worry about it.

I have no idea where the .bin comes from in the java instruction pages. I downloaded a tar.gz file, not a .bin file.

Sam.

---

### Post by Cavsfan on 2012-05-17
> **samwillc said:**
> Lol, don't worry about it.

I have no idea where the .bin comes from in the java instruction pages. I downloaded a tar.gz file, not a .bin file.

Sam.

So, you got it completed?

---

### Post by samwillc on 2012-05-17
Gonna try tomorrow, will remove java and try again.

Will post the results. :)

Sam.

---

### Post by sammiev on 2012-05-17
Surprised the thread was not marked as solved yet. Glad you have it working.

---

### Post by samwillc on 2012-05-18
Was trying to install manually but still can't get it working from the tar.gz file!

Forget it, got java installed from [http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

Works fine. Thanks for all the help everyone.

Sam.

**ps - I can't mark as solved - didn't start the thread **

---

### Post by Cavsfan on 2012-05-18
> **sammiev said:**
> Surprised the thread was not marked as solved yet. Glad you have it working.

Solved? It's meant as sort of a how to. (re-read the 1st post) How to install the latest Java the CLI way.
The links aren't mine. I have been putting these up when a new version of Java came out.
I think I counted 10 threads I have created for people to get the latest version of java.
Most of the time, no one has any issues installing. It only took me about 10 minutes to do it myself.
I prefer CLI to adding a ppa because I am _*usually*_ a few to several days ahead of the ppa.

> **samwillc said:**
> Was trying to install manually but still can't get it working from the tar.gz file!

Forget it, got java installed from [http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

Works fine. Thanks for all the help everyone.

Sam.

**ps - I can't mark as solved - didn't start the thread **

For those that cannot figure out the CLI way there is the ppa way.
Glad you figured it out.

---

### Post by samwillc on 2012-05-19
> **Cavsfan said:**
> Glad you figured it out.

Your help was most appreciated, thanks.

Sam.

---

