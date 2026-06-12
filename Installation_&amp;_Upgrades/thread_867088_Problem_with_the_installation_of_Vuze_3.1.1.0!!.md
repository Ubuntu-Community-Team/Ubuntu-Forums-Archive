---
title: "Problem with the installation of Vuze 3.1.1.0!!"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by libe on 2008-07-22
Can anyone guide me through the installation process of the new Azureus client-renamed Vuze!
I did exactly as the ["How to"](http://ubuntuforums.org/showthread.php?t=144546&highlight=installing+vuze) instructs but with no results!
I don't have the given output from the terminal but told me something about sun java and the strange thing is that it's been already installed successfully!
Any help appreciated!
Thx in advance!

---

### Post by Partyboi2 on 2008-07-23
> I don't have the given output from the terminal but told me something about sun java and the strange thing is that it's been already installed successfully! Can you provide the output you are having problems with?
what happens when you type vuze in the terminal?

---

### Post by fs3rp4 on 2008-07-23
Do you have this package installed?   


sun-java6-jre

---

### Post by libe on 2008-07-23
> Can you provide the output you are having problems with?
what happens when you type vuze in the terminal? 
```

***@***-desktop:~$ sudo tar jxvf Vuze_3.1.1.0_linux.tar.bz2 -c /opt/
[sudo] password for ***: 
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
***@***-desktop:~$ 
```

> **fs3rp4 said:**
> Do you have this package installed?   
sun-java6-jre
Yes

---

### Post by Partyboi2 on 2008-07-23
You need to use a capital [COLOR=Red]C[/COLOR] not a lower c
so try 
```
sudo tar jxvf Vuze_3.1.1.0_linux.tar.bz2 -[COLOR=Red]C[/COLOR] /opt/
```

---

### Post by libe on 2008-07-23
> **Partyboi2 said:**
> You need to use a capital [COLOR=Red]C[/COLOR] not a lower c
so try 
```
sudo tar jxvf Vuze_3.1.1.0_linux.tar.bz2 -[COLOR=Red]C[/COLOR] /opt/
```
This is what i'm getting now:
[code}***@***-desktop:~$ tar: Vuze_3.1.1.0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/code]

---

### Post by Partyboi2 on 2008-07-23
> **libe said:**
> This is what i'm getting now:
[code}***@***-desktop:~$ tar: Vuze_3.1.1.0_linux.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/code]
make sure you are in the correct directory, so if the vuze file you downloaded is on your Desktop in the terminal type
```
cd ~/Desktop
``` then extract
```
sudo tar jxvf Vuze_3.1.1.0_linux.tar.bz2 -C /opt/
```

---

### Post by libe on 2008-07-24
I'm already in the correct directory which is "desktop",just take a closely look at the previous output "***@***-desktop:~$"!
What the F@@@?

---

### Post by Partyboi2 on 2008-07-24
Lets see if I can explain this another way. When I open a terminal the prompt looks like this:
> karl@karl-desktop:~$  This is my /home directory. This is not my Desktop directory. If I was to get a list of what is in this directory I would type:
```
ls
``` I would see that it does not list the package I am wanting to extract. But If I wanted to change to my Desktop directory I would type: 
```
cd ~/Desktop
``` That is Desktop with a capital D, my prompt would now look like this:
```
karl@karl-desktop:~/Desktop$ 
```and then typed
```
ls
``` I would see the files that are on my Desktop including the Vuze_3.1.1.0_linux.tar.bz2 file that needs to be extracted. :)

---

