---
title: "Installing 10 on a dualboot machine"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by alexee on 2010-10-21
I want to install Ubuntu 10 on a machine that already has Windows and an old version of Ubtunu on it.

I burned a live CD and ran it but it gives the error:

(iniramfs) mount: mounting /dev/loop0 on //filesystem:squashfs failed input output error.
Can not mount,

---

### Post by lindsay7 on 2010-10-21
Are you sure that you burned the iso image and not just copied the files to a cd?

---

### Post by alexee on 2010-10-21
The CD is working. I see a Ubuntu logo at the bottom of the screen. It stops. I see this message.

---

### Post by Rubi1200 on 2010-10-21
Hi and welcome to the forums :)

Try downloading the image again and do an MD5SUM on it before burning at the lowest possible speed for best results.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

When you start the CD you can also hit Enter and select the option to check the disc for defects.

---

### Post by alexee on 2010-10-21
I did the burn at 4..7, the lowest speed I was offered. 

I'll try it again with [enter] and also this check.

---

### Post by na5h on 2010-10-21
Hi! Yes, you should probably try to download and burn the image again. I've had some problems with burning cd-images myself in the past. If you use Windows, Infrarecorder ([infrarecorder.org]("http://infrarecorder.org")) is a good, free software for burning cd-images. It has always worked for me! I've had a few problems with burning cd-images correctly with Brasero (Ubuntu's standard disc-burner).

---

### Post by alexee on 2010-10-21
A friend told me not to bother trying to burn my own but to just order the Ubunu CD by post. He said in the past he had no end of problems trying to burn CDS for Ubunu installs.

I wondered if my CD drive might not be working great because I rarely use it? I really hate CDs (so easily damaged) and just use USB drives now which are way bigger anway.

I wanted to make a live USB but it seems you can only do this if you have Ubuntu 10 already installed.

---

### Post by Rubi1200 on 2010-10-21
Not entirely true.

Do you have Windows installed or can you access a Windows machine?

Then check out UNetbootin; has always worked great for me (on Ubuntu since I don't use Windows).
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by alexee on 2010-10-21
I'm trying UNetbootin now on Ubuntu. I try to change the permissions to 'execute' but it says 'you are not the owner and do not have the permissions' even though I just downloaded it two minutes previously :confused:

---

### Post by Rubi1200 on 2010-10-21
> **alexee said:**
> I'm trying UNetbootin now on Ubuntu. I try to change the permissions to 'execute' but it says 'you are not the owner and do not have the permissions' even though I just downloaded it two minutes previously :confused:
The program is available in the repositories, so you should not need to download the package from the website.

Search in Synaptic for it and then install.

---

### Post by alexee on 2010-10-21
I opened 'Add/Remove Applications' and could not find it even when I opened all the parameters.

---

### Post by Rubi1200 on 2010-10-21
Sorry, I am confused :confused:

Are you in Windows or Ubuntu now?

Which version of Windows and did you install Ubuntu using Wubi?

---

### Post by alexee on 2010-10-21
Ubuntu. I keep saying that. I am not sure why people keep telling me what to do in Windows. I only said it was dual boot in case that affected the mounting. 

I click the orange circle at the top and among the options are 'Add/Remove Applications'. After that is 'Places' and 'System'. Maybe I should also be looking there for how to add this programme?

I didn't install the Ubuntu, the previous owner did. They gave me some CDs in case I needed to fix it but they are a bit scratched now.

---

### Post by Rubi1200 on 2010-10-21
Are you able to run it from the terminal? The terminal can be found by looking at Applications > Accessories > Terminal.

```
unetbootin
```Also, if it was somehow installed to a non-default location, try this:

```
locate unetbootin
```And I apologize for the confusion.

---

### Post by alexee on 2010-10-21
I found this Synaptic while looking for the terminal. Not sure why there are two ways of adding packages but there you go. I had a look there are nothing.

In terminal the first gives 'command not found'. The second responds as if I did nothing. No feedback, negative or positive.

---

### Post by Rubi1200 on 2010-10-21
> **alexee said:**
> I found this Synaptic while looking for the terminal. Not sure why there are two ways of adding packages but there you go. I had a look there are nothing.

In terminal the first gives 'command not found'. The second responds as if I did nothing. No feedback, negative or positive.
There is more than one way to install and manage packages in Ubuntu, but that is another story.

It seems the program was not installed and if you do not have administrative rights there is not much you can do.
> I didn't install the Ubuntu, the previous owner did.Did he/she give you the admin password?

 > I try to change the permissions to 'execute' but it says 'you are not  the owner and do not have the permissions' even though I just downloaded  it two minutes previouslyThis now makes sense, since if you do not have admin rights you will be unable to change permissions, install software, administer the system etc.

Please clarify what rights you have on the system so we can help you achieve what you want to do.

Thanks.

---

### Post by alexee on 2010-10-22
No, I do have this password. I've had this problem a long time. Sometimes it recognises I am login in as admin and sometimes not. It seems complete capricious. Never asks for a prompt if it does have a problem either.

---

### Post by Rubi1200 on 2010-10-22
Hi alexee,
so let's try a couple of things to get this resolved.

First, from a terminal (which you can find under Applications > Accessories) post the output of the following commands:
```
groups
cat /etc/passwd | grep <your_user_name>
```Substitute the user-name for whatever you use to login to the computer e.g. alexee

Next, try and install the program, again from the terminal, using the following command:
```
sudo apt-get install unetbootin
```Report any problems.

Thanks.

---

### Post by alexee on 2010-10-22
I type it all on one line, I get:

id: cat: No such user
id: /etc/passwd: No such user

If I type it as two lines I get for the first (groups):

alexee adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin netdev powerdev

for the second (cat /etc/passwd | grep):

alexee:1000:1000:Alexee,,,:/home/alexee:/bin/bash

---

### Post by Rubi1200 on 2010-10-22
It seems as if you have enough rights to administer the system.

Did you try running the command I gave you to install the program?

---

### Post by alexee on 2010-10-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package unetbootin

:(

---

### Post by Rubi1200 on 2010-10-22
If you already tried the commands here [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install) to get it to run and it didn't work, I am not sure what to suggest. Maybe try loading the image onto a USB from another computer?

---

### Post by ronparent on 2010-10-22
He could install unetbootin to a live cd session and use it to place the unetbootin on a usb key. Unetbootin is installable thru sysnaptics from the 10.10 cd. The installation would only last as long as the ssession which could be long enough to accomplish his objective.

---

### Post by Rubi1200 on 2010-10-22
@ronparent: I like the idea, the only problem is that the OP already mentioned having difficulties getting a LiveCD to work, which is where the whole install to a USB idea came into the picture.

Are there any other options?

---

### Post by alexee on 2010-10-22
Just downloaded and installed the Windows version of UNetbootin. Thirty seconds work :oops: I guess I'll keep the Windows partition if I do get Ubuntu installed :-#

I used UNetbootin to install the ISO to the USB. When I have the USB plugged in on startup nothing new happens as it would if I had an install CD in the CD drive. 

Looking at the USB in Windows I see Wubi.exe. If I click on that, for some reason, it has decided to work in French. Haven't a clue what it says and there is no option to change language.

---

### Post by ronparent on 2010-10-22
If the OP has difficulty getting the live cd to work, that should be fixed before anything else is done. The installed system would most likely not run for the same reason the cd won't boot. Which is why I suggest that needed boot parameters be found before any install is attempted.

---

### Post by alexee on 2010-10-25
I was hoping someone might explain why the download decides to automatically work in French. I am in Brussels but Dutch and German are also official languages in Belgium ](*,)

Anyway, thanks for the advise Ron. How to I find the 'needed boot parameters'. And what are they?

---

### Post by alexee on 2010-11-25
As nobody responded I gave up and sent away for the CD. I installed this this morning. I had hoped it would have a user friendly interface but it was quite difficult to understand.

I choose the option, install alongside other operating systems. This then gave me the option for what size to make 'Ubuntu 7.0'(i choose the minimum 6Gb, there was no option of overwriting it) and what size to make 'Ubuntu' (it didn't say 10.10 but I had to presume it meant that). 

It installed fine but the problem is I can no longer boot Windows. I defineitly didn't overwrite the whole disk as it made my Ubuntu partion 30Gb and my disk is 160Gb. Is there any possibility in the 'install alongside other operating systems' that one can damage a Windows partition?

---

### Post by Rubi1200 on 2010-11-25
I'm sorry you had to go through this to get Ubuntu installed, but sometimes there are reasons why it won't work which do not seem to have any logical explanation.

Anyway, since you now have another problem, let's focus on resolving it.

From either within the Ubuntu installation or a LiveCD, post the results of the boot info script linked at the bottom of my post (instructions on what to do are also there).

> Is there any possibility in the 'install alongside other operating systems' that one can damage a Windows partition? 	
Unfortunately, the answer is yes. Resizing partitions in Windows 7 needs to be done from within Windows.

However, let's first see the results before jumping to conclusions; it may just need a simple fix with the bootloader to get things up and running again.

---

### Post by alexee on 2010-11-25
I ran the Windows Recovery process and it seems to have fixed it. Thanks!

It really is very annoying the way the installer is so lacking in user friendliness. Just not even to think to name the new install 'Ubuntu 10.10' rather than simply 'Ubuntu' is very sloppy. 

There needs to be a one step rewrite my old Ubuntu with new Ubuntu option. I am now wasting 6Gb of my harddrive on the obsolete system.

---

### Post by Rubi1200 on 2010-11-25
I am glad you got things sorted out :)

If you would like to voice an opinion about the installer based on your experiences, you might want to consider joining the ubuntu-installer mailing list where you can then comment on things like this.
[https://lists.ubuntu.com/mailman/lis...untu-installer]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-installer")

---

### Post by alexee on 2010-11-26
Strange. It did it again this morning. Again I ran the recovery process and everything was OK.

---

### Post by Rubi1200 on 2010-11-26
alexee,
do yourself, and us, a favor and run the boot info script I mentioned in a previous post.

The results will tell us what is where and will make troubleshooting this issue a lot easier.

Thanks in advance.

---

