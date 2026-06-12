---
title: "Wireless isn't working in Karmic"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Virtualboxbuntu on 2009-06-22
Hello,

I am running Kubuntu 9.10 Alpha 2. I do release it's an alpha, but I still hope that someone could help me with my problem.

You see, I have a DLink wireless adapter that works perfectly fine in Linux Mint 6, both the gnome and KDE versions. I decided to install Kubuntu Karmic and try it out. 

I enter my WPA key to connect to my wireless network, but it keeps prompting me for the key, as if it were incorrect. But I copied the key exactly from my laptop, which I am using now, therefore it is the correct key. Is there any way to make it connect properly?

---

### Post by dBuster on 2009-06-22
Might find better luck posting and or searching in this forum:

[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

It is the development forum for Karmic...

---

### Post by LKjell on 2009-06-22
Hi I am assuming you use WPA Personal. Usually when you type in a passkey and then want to see what the key is afterwards it will be decrypted. Therefore you need to remember the key you set in the router. If you cannot remember then I suggest to set a new one in the router.

As a good tedious practise resetting the passkey in the router is a good way to check whether you have it correctly or not.

---

### Post by Zorael on 2009-06-22
The KDE network manager applet had some issues with WPA networks earlier. I'd *wager* they're fixed by now, but you might want to try **wicd**, just in case.

The repos seem to contain the newest version (1.5.9).

---

### Post by Virtualboxbuntu on 2009-06-22
@LKjell: I use WPA personal. I copied the key exactly from my laptop, which is connected to the Internet. It is the correct key because it works on the laptop.

@Zorael: OK, I will try wicd.

In case it isn't clear, it's my desktop that has Karmic on it. And thank you to whoever moved this to the proper forum.

---

### Post by Hated On Mostly on 2009-06-22
Probably a hidden extra character due to the copy and paste of the key. You either need to delete the extra character or manually type the key. I have seen this happen a lot. The key looks correct in the text file you have it saved in, but there is an extra character that you can't see. Sometimes you can see it by copy/pasting the key in another application or in Wordpad/Notepad in Windows.

---

### Post by novafluxx on 2009-06-22
> **Virtualboxbuntu said:**
> Hello,

I am running Kubuntu 9.10 Alpha 2. I do release it's an alpha, but I still hope that someone could help me with my problem.

You see, I have a DLink wireless adapter that works perfectly fine in Linux Mint 6, both the gnome and KDE versions. I decided to install Kubuntu Karmic and try it out. 

I enter my WPA key to connect to my wireless network, but it keeps prompting me for the key, as if it were incorrect. But I copied the key exactly from my laptop, which I am using now, therefore it is the correct key. Is there any way to make it connect properly?

I have this exact same problem in Kubuntu 9.04 on my Dell Inspiron 1318 notebook. Its a KDE(?) problem, not just Karmic. Not sure how to connect it, I gave up and went back to GNOME with Ubuntu 9.04.

---

### Post by Virtualboxbuntu on 2009-06-22
> **Hated On Mostly said:**
> Probably a hidden extra character due to the copy and paste of the key. You either need to delete the extra character or manually type the key. I have seen this happen a lot. The key looks correct in the text file you have it saved in, but there is an extra character that you can't see. Sometimes you can see it by copy/pasting the key in another application or in Wordpad/Notepad in Windows.
I have also entered the key manually.

could somebody give me a link to the deb for wcip, so i can download it with my laptop?

---

### Post by Zorael on 2009-06-22
Isn't it in the respositories? ([http://packages.ubuntu.com/karmic/wicd](http://packages.ubuntu.com/karmic/wicd))

```
$ sudo aptitude install wicd
```

It may/will want to remove NetworkManager, since it replaces it.

---

### Post by Virtualboxbuntu on 2009-06-23
In case you haven't realized it, my entire problem is that I don't have any Internet on that computer. How am I supposed to get it through APT?

EDIT: Sorry, I think I forgot to mention that there was no wired Internet available.

ANOTHER EDIT: Never mind, I found it on Sourceforge. I will let you know if it works.

UPDATE: I have many dependencies to figure out. Since there is no Internet on my desktop, everything must be manually downloaded to my laptop first.

---

### Post by Virtualboxbuntu on 2009-06-23
OK, I installed WICD and all of its dependencies.
I run wicd-client and I get a lot of errors.
I run wicd and it says it needs root privileges.
I run sudo wicd and it says /var/run/wicd/wicd.pid

Nothing happens after that. What's going on?

---

### Post by novafluxx on 2009-06-23
You should use a system with a network connection, and use synaptic(?) to generate a script, it will download the packages, and dependencies and you can then put them on a disc or flash drive, then install them from that disc, and dependancies resolved!

I'm not sure how to do this step-by-step, however I do believe its possible

---

### Post by Virtualboxbuntu on 2009-06-23
I resolved all the dependencies, but I still get the problems I mentioned above.

---

### Post by Virtualboxbuntu on 2009-06-23
Never mind about this. I'm just going to use Linux Mint 7 instead. Mint is the only distro that has ever worked with all my hardware perfectly, except for having to install drivers through the drivers manager.

---

