---
title: "Google chrome ppa missing."
date: 2016-12-05
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-12-05
Somehow I got google chrome 55 installed, but I just noticed in other sofware there is no ppa listed.  Went to google and did the following and it is screwed up:

```
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'
henry@wyatt:~$ clear

henry@wyatt:~$ wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
```

So the ppa is there but I deleted it.  I just do not know how to get rid of the key.

Henry

---

### Post by vasa1 on 2016-12-05
Hi,

Please use **[noparse]```
[/noparse]** and **[noparse]
```[/noparse]** tags to enclose *terminal output*. The reason is that terminal output (usually) uses a fixed-witdh font so that columns are properly aligned and spaced.

[LIST]
[*]*If you start a new thread*, just select the text you've pasted and click on the **[SIZE=4]#[/SIZE]** icon above the text box _or_ first click the **#** icon and then paste the terminal output between the code tags.
[*]*If you reply to a post by clicking the large **+Reply to Thread** below the last post in a thread*, the same process applies.
[*]*If you reply to any post by clicking on "Adv Reply" or "Reply With Quote"*, the same applies.
[*]However, *if you click on "Quick Reply"*, you'll see fewer icons above the text area and the **#** icon will be missing. In that case, either type in the [noparse]```
[/noparse] and [noparse]
```[/noparse] tags yourself for each bit of terminal output or click on "Go Advanced" to give you all the editing options the forum provides including the **#** icon.
[/LIST]

---

### Post by howefield on 2016-12-06
Try loading up the Software & Updates application, then from the Authentication tab you should see the Chrome key.. highlight and remove.

---

### Post by Hewjr100 on 2016-12-06
There are 2 keys listed, but, several attempts to remove them failed.  I had to remove google chrome via sudo nautilus, because software center, did not remove it.

Henry

[ATTACH=CONFIG]272571[/ATTACH]

---

### Post by howefield on 2016-12-06
> **Hewjr100 said:**
> There are 2 keys listed, but, several attempts to remove them failed.

It really is as easy as highlighting the offending keys and pressing the remove button.

Alternatively, what is the output from the terminal command..

```
sudo apt-key list
```

You can delete from the terminal with..

```
sudo apt-key del key_id
```

I'd suggest you don't use the second command it without posting the output to the first command beforehand.

> I had to remove google chrome via sudo nautilus, because software center, did not remove it

This doesn't make sense, how did you remove chrome with nautilus ?

---

### Post by Hewjr100 on 2016-12-06
Yep I did highlight hit enter, entered password, and hit enter over and over again.  Sudo nautilus, enter password and got to /opt highlight and delete.

```
$ sudo apt-key list
[sudo] password for henry:          
/etc/apt/trusted.gpg
--------------------
pub   dsa1024 2007-03-08 [SC]
      4CCA 1EAF 950C EE4A B839  76DC A040 830F 7FAC 5991
uid           [ unknown] Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   elg2048 2007-03-08 [E]

pub   rsa4096 2016-04-12 [SC]
      EB4C 1BFD 4F04 2F6D DDCC  EC91 7721 F63B D38B 4796
uid           [ unknown] Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   rsa4096 2016-04-12 [S] [expires: 2019-04-12]

/etc/apt/trusted.gpg.d/libreoffice_ubuntu_ppa.gpg
-------------------------------------------------
pub   rsa1024 2010-12-29 [SC]
      36E8 1C92 67FD 1383 FCC4  4909 83FB A175 1378 B444
uid           [ unknown] Launchpad PPA for LibreOffice Packaging

/etc/apt/trusted.gpg.d/ubuntu-keyring-2004-archive.gpg
------------------------------------------------------
pub   dsa1024 2004-09-12 [SC]
      6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid           [ unknown] Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   elg2048 2004-09-12 [E]

/etc/apt/trusted.gpg.d/ubuntu-keyring-2004-cdimage.gpg
------------------------------------------------------
pub   dsa1024 2004-12-30 [SC]
      C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid           [ unknown] Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-archive.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      790B C727 7767 219C 42C8  6F93 3B4F E6AC C0B2 1F32
uid           [ unknown] Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

/etc/apt/trusted.gpg.d/ubuntu-keyring-2012-cdimage.gpg
------------------------------------------------------
pub   rsa4096 2012-05-11 [SC]
      8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid           [ unknown] Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

henry@wyatt:~$
```

Here is the output:

```
henry@wyatt:~$ sudo apt-get del key_id
E: Invalid operation del
henry@wyatt:~$
```

Henry

---

### Post by howefield on 2016-12-06
How many times have you to be requested to use code tags for terminal output, what is so unreasonable about using them that you persistently refuse ?

I got the command wrong, my apologies and have fixed my last post. You should use the actual key ID for the repository you want to remove, not the word "key_id".  

Deleting folders in Nautilus is generally an exceptionally poor way of removing applications, I'd suggest you don't.

---

### Post by Hewjr100 on 2016-12-06
How about you having some patience I am trying to figure tags out. I am not an expert in everything.

Henry

Btw the I was asked only once, not many times.  I will practice using tags, until then I will not post terminal output anymore.

Henry

Used key as you instructed, but I recieved error message:

invalid operation del

Henry

How about if I copy and paste terminal output to libreoffice writer, adjust it, then copy and past to my posts/replies from libreofice writer.

Henry

---

### Post by QIII on 2016-12-06
How about if you use code tags, as you have been asked more than once?  This is not your only thread, nor is this the first time you have been asked and instructed.  In this thread you have been given clear instructions.

Code tags make it much easier to help you because the output is left in its original format, which is sometimes important.

---

### Post by Hewjr100 on 2016-12-06
Btw howefield I do expect an apology for your quick, and spiteful retort, that was incorrect, only in this thread I was asked to use "Tags". Only once until you jump on me with an attitude.

Henry

---

### Post by QIII on 2016-12-06
You have also been asked by slickymaster recently.  slickymaster even provided you a link to instructions.

---

### Post by howefield on 2016-12-06
> **Hewjr100 said:**
> Btw howefield I do expect an apology for your quick, and spiteful retort, that was incorrect, only in this thread I was asked to use "Tags". Only once until you jump on me with an attitude.

Get a grip of yourself.

You have been requested to use code tags multiple times, firstly in the Posting Tips which form part of the forums Code of Conduct, in at least 3 threads in the past week alone - I haven't checked further back than that, and also in many edited posts where the reason is given as "please use code tags". Seems a simple enough request to comply with that benefits both yourself and others who may wish to help.

There will be no apology coming from where I'm sitting any time soon, so please don't hold your breath. I'm out of here except if the need to further moderate your posts occurs.

---

### Post by vasa1 on 2016-12-06
Here's one from [The Intel Graphics Update Tool for Linux v2.0.3]("https://ubuntuforums.org/showthread.php?t=2344530")

---

### Post by Hewjr100 on 2016-12-06
Dear howefield I am sorry for my post, but let me explain.  I am a 30 retired US Army.  I served with the 3rd Infantry Division in Iraq, and the 82nd Airbourne Division in Afghanitsan.  I suffered a minor brain injury, but over time it effects my memory.  Please accept my apologies.

Henry

PS  I was able per your instructions to remove keys, thanks for your help.

---

