---
title: "uninstall 12.10 and install 12.04"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by facetious on 2013-01-10
Hi all,
New to Linux but I Installed Ubuntu 12.10 a few days ago as a second OS along with Windows 7 Home. Apart from having great difficulty finding my way around, I have don't seem to be able to download any programs (apps?) from the ubuntu software centre.

On reading some posts, I see that people prefer 12.04 to 12.10 as they say it is more stable. perhaps, as a newbie to linux I should have 12.04.

How would I go about uninstalling 12.10 and installing 12.04?

Many thanks

---

### Post by howefield on 2013-01-10
> **facetious said:**
> I have don't seem to be able to download any programs (apps?) from the ubuntu software centre.

What's the problem / error ?

> How would I go about uninstalling 12.10 and installing 12.04?

How did you install it in the first place ? If a dual boot on its own partition, you can clean install over the existing partition.

---

### Post by facetious on 2013-01-10
While in Windows, I created a spare partition. Then, I installed 12.10 using wubi.exe, selecting the new drive.  It was really easy.

C: Drive contains Windows
G: Drive I created for all my own work files and folders (thus leaving C: drive as only containing the OS.
H: Drive has Ubuntu 12.10

I presume wubi created the screen where I select which OS I want. 

Problems I am encountering include not being able to add new programs. This occurs even though I use the Ubuntu download centre. I have tried to add programs like LibreOffice database and Wine. Both these have been unsuccessful.

12.10 also seems to "lock up" - the screen dims and stays that way for maybe 20-30 seconds and an timing icon appears, as though something was being saved (but no request was made to save anything), though sometimes if I click on a different program in the quick launch bar, I can go to the new program after a second or two.

---

### Post by howefield on 2013-01-10
As I understand Wubi, it can be uninstalled via the Control Panel in Windows > Add/Remove Programs.

Try updating the software sources by opening a terminal and using the following command and see if that gives you the ability to download applications via the Software Centre.

```
sudo apt-get update
```

---

### Post by facetious on 2013-01-10
Thanks for the help, howefield.

Yes, I have found Wubi in my windows uninstall - under the name Ubuntu and some 4 gb in size.

However, back in Ubuntu, I cannot find the "Terminal", to check as advised. The only programs that I can find are on the launch bar on the left of the screen and a few more on the Dash Home. And I think there are quite a few more programs which are listed as installed in the Ubuntu Software center> installed. But there is no indication as to where they are to be found.

Ubuntu is definitely not as user friendly as Windows.

---

### Post by howefield on 2013-01-10
> **facetious said:**
> Ubuntu is definitely not as user friendly as Windows.

I suppose you just sat down at a computer with Windows installed on it all those months/years ago and was an instant expert. Most people have a learning curve to go through, it is no differnet with Linux.

Press the Super key, (the one with the Windows logo on it, I'm sure you'll know it) or the top most icon on the launcher and start typing the word terminal, the icon for it should appear after typing a few of the letters, click on it to load it.

---

