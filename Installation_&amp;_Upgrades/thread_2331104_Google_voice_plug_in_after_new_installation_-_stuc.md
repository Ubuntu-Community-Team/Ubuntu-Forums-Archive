---
title: "Google voice plug in after new installation - stuck"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2016-07-18
Hi, 

After having problems with upgrade from 14.04 I finally decided to wipe my computer and install a clean new 16.04 

That done, I am now installing the apps that I need. 

I am working with reinstalled firefox web browser. Trying to make a phone call via google voice from my gmail page. I get a notice that a plug in is needed. So I hit the link. 

Then I approve download:

and install:

and here the installation of the plug in gets stuck:

What do I need to do to complete the installation?

---

### Post by niceguy123 on 2016-07-19
Please notice that after the listed above, there is a box on the left hand bar showing a installation process, when I hover the mouse over it I see "waiting to install", but, that doesn't change.

---

### Post by niceguy123 on 2016-07-25
I have been having a problem with this and also not been able to post to the forum.


Waiting to install.... and still waiting, but nothing happens. 


I have a new installation of Ubuntu 16.04

Now trying to install a google hangouts plugin on firefox.

I keep ending up with a message "Waiting to install" but, noting happens and it doesn't install.

I then tried installing google chrome and got the same message.

Do I need to configure Software & Setting to allow 3rd party software?

If so, how do I do that?

---

### Post by howefield on 2016-07-25
Duplicate threads merged.

---

### Post by niceguy123 on 2016-07-25
Thanks @howefield, 

I couldn't figure out how to delete a thread either. 

Any idea where to find info to solve my problem above?

---

### Post by howefield on 2016-07-25
> **niceguy123 said:**
> I couldn't figure out how to delete a thread either. 

You can request a thread be deleted by reporting it.

> Any idea where to find info to solve my problem above?

I have a pristine installation of 16.04 so tried to install the add-on, and it worked a treat. Are you trying to install the downloaded plugin (.deb file) with the Software centre by any chance ?

---

### Post by niceguy123 on 2016-07-27
> **howefield said:**
> You can request a thread be deleted by reporting it.



I have a pristine installation of 16.04 so tried to install the add-on, and it worked a treat. Are you trying to install the downloaded plugin (.deb file) with the Software centre by any chance ?

Yes. Should I be doing this in a different way?

---

### Post by howefield on 2016-07-27
> **niceguy123 said:**
> Yes. Should I be doing this in a different way?

Well, no, ordinarily you should be able to install 3rd party debs with the Software Centre but there has been an issue lately where the Software Centre doesn't install. I'm not sure of the current state of that bug.

However, you can install the google plugin by using the terminal with... (assuming the deb is in the Downloads folder and the name is the same, otherwise change to suit)

```
sudo apt install ~/Downloads/google-talkplugin_current_amd64.deb
```

---

### Post by niceguy123 on 2016-07-27
```
1234@1234:~$ sudo apt install ~/Downloads/google-talkplugin_current_amd64.deb
[sudo] password for 1234i: 
Sorry, try again.
[sudo] password for 1234: 
Reading package lists... Done
E: Unsupported file /home/haivri/Downloads/google-talkplugin_current_amd64.deb given on commandline
```

---

### Post by howefield on 2016-07-27
Do you have a 64 but operating system ?

```
uname -a
```

---

### Post by niceguy123 on 2016-07-27
Yes.


```
1234@1234:~$ uname -a
Linux 1234 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by howefield on 2016-07-27
OK, what is in your Downloads folder ?...

```
ls -al ~/Downloads/google*
```

---

### Post by niceguy123 on 2016-07-27
```
1234@1234:~$ ls -al ~/Downloads/google*
ls: cannot access '/home/haivri/Downloads/google*': No such file or directory

```

---

### Post by howefield on 2016-07-28
> **niceguy123 said:**
> ```
1234@1234:~$ ls -al ~/Downloads/google*
ls: cannot access '/home/haivri/Downloads/google*': No such file or directory

```

So, change the path of the apt command to suit where the file is located...

I can only replicate the error "E: Unsupported file.... given on commandline" by using an incorrect file name or path.

---

### Post by niceguy123 on 2016-07-28
```
niceguy123@niceguy123:~$ ls -al ~/Downloads/apps
total 7640
drwxrwxr-x 2 niceguy123    4096 &#1497;&#1493;&#1500; 28 17:41 .
drwxr-xr-x 6 niceguy123    4096 &#1497;&#1493;&#1500; 28 17:41 ..
-rw-rw-r-- 1 niceguy123 7813320 &#1497;&#1493;&#1500; 28 17:39 google-talkplugin_current_amd64.deb

```

---

### Post by howefield on 2016-07-28
Does this work then..

```
sudo apt install ~/Downloads/apps/google-talkplugin_current_amd64.deb
```

---

### Post by niceguy123 on 2016-07-28
Thank you @howefield that worked. Your help is much appreciated.

---

### Post by howefield on 2016-07-28
Cool, glad to hear it.

The Software Centre should be installing 3rd party debs shortly, if it isn't already, but in any event there is always *apt install* to fall back on when installing locally stored .deb files in a 16.04 installation.

---

### Post by niceguy123 on 2016-07-28
How do I add "solved" to the title of this thread?

---

### Post by howefield on 2016-07-28
> **niceguy123 said:**
> How do I add "solved" to the title of this thread?

Thread tools, near the top of the page.

---

