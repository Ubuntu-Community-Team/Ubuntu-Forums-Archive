---
title: "Updates downloaded but will not install"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by SUPERFITTER on 2012-06-03
I have 11.10 installed and have not had any problems updating until now. 

I get this message when I run Update Manager:
55 updates are ready to install.  Updates have already been down loaded, but not installed.

I click: Install up dates

It then asks for Ubuntu 12.04 disk to be placed in optical drive, which I do.

I then get this message:
Failed to download package files.
Check your Internet connection.

My Internet connection works just fine.

Any suggestions, as to my next step?

---

### Post by dino99 on 2012-06-03
you need to deactivate that cd entry line into /etc/apt/sources.list (comment it out)

---

### Post by SUPERFITTER on 2012-06-03
> **dino99 said:**
> you need to deactivate that cd entry line into /etc/apt/sources.list (comment it out)
 
How do I do that?

---

### Post by Lorin Ricker on 2012-06-03
> How do I do that?

Generally, to edit a text (configuration) file that is owned by root (that is, a "system config" file, etc.), you need to use an editor that has been launched by **sudo**.  This is typically done by prefixing your editor command with **gksudo** (see **man gksudo**).

So, pick your favorite text editor -- using gedit here just as an example, but you could nano, or vim, or emacs, if you wanted to -- thus:
```

$ gksudo gedit /etc/apt/sources.list

```

Note that, at this point, you've got a text editor open with full sudo (root) privileges, hacking the file in question -- **and** you *could*, if you want, open additional system text files in other tabs and have your way with 'em.  Hey, it's your system... your responsibility.

Back to /etc/apt/sources.list -- it's likely that the line you're looking for is either the first one, or near the top, and begins with the text "deb cdrom:[Ubuntu 12.04 LTS"... Commenting it out just means to enter (type) a pound-sign "#" as the very first character of that line, so it now looks thus:

```
#deb cdrom:[Ubuntu 12.04 LTS ...
```

Having made just that one change, you can save-file-&-exit.  You're done.

Having gone through all of this for your /etc/apt/sources.list file, there's also a GUI-tool-way to do this.  Just open your **Update Manager** and click on the **Settings** button (lower left-corner) to bring up the ***Software Sources*** dialog box.  On the Ubuntu Software tab, _uncheck_ the "Cdrom with Ubuntu 12.04 'Precise Pangolin' - Officially supported - Restricted copyright" checkbox (you'll have to enter your authorization password in a prompt-box, just as if you were doing a sudo command), which disables the same text option in /etc/apt/sources.list ... *Done.* (Confirm that this actually does the same thing as editing the file by doing "sudo cat /etc/apt/sources.list" before and after unchecking the box.)

So, two ways of doing the same thing... Hope this helps demystify a few things for you.  -- Lorin

---

### Post by SUPERFITTER on 2012-06-04
Thank you,  dino99 and Lorin Ricker for your response to my problem. 

 I unchecked the box and ran the Update Manager and all is good.  I downloaded Ubuntu 12.04 'Precise Pangolin' but I did not install.  I don't know how that box would have been checked?

Problem Solved and thank you both again! ):P

---

