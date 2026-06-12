---
title: "New 2 Ubuntu, Help Me Keep My Sanity"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by dave44 on 2008-06-11
I have been desperately trying to install a couple of my Microsoft programs now that I have switched over.  I would like to install Encarta 2008 Premium and Battlefield 2.  I have read a lot of the post and there are many that say "Oh just this" or "have you tried doing", this is all new 2 me and I really need somebody to give me the simple down and dirty, COMPLETE instructions.

I GREATLY APPRECIATE your help.

Dave44

---

### Post by avtolle on 2008-06-11
These are Windows programs. They will not run under Linux natively. One method is to install WINE and see if they run under WINE. Another is to run windows under a virtual machine and access the programs you want this way. The third way is to dual boot Windows and Ubuntu, using Windows to access the programs. I've a feeling you have seen these solutions, and don't like them. Just remember that Linux (Ubuntu or otherwise) isn't Windows and *vice versa*.

---

### Post by avtolle on 2008-06-11
First, let me apologize for the blast above. Been a hard day already.

When you have asked before, what have people recommended you do? What do you not understand from their responses? 

Again, you will not be able to install the Windows apps you posted in Ubuntu and have them "just run". You'll need to do one of the three things I posted earlier. Perhaps someone other than I should take over now, as I don't use Windows apps.

---

### Post by issih on 2008-06-11
Easiest place to start is to try using wine, which attempts to run windows applications on linux by mapping windows system calls onto linux ones.

Install it by going to :

Applications->Add/Remove

In the resulting application, ensure that the drop down is set to show all available applications then type "wine" into the search box in the top right of the window.

Click on the little check box next to "Wine Windows Emulator" then hit the "Apply Changes" button.

Once the software is installed you should have some new menu entries for wine under the applications menu (if they are missing try restarting X with ctrl-alt-backspace).

Now you install the windows program into your "virtual" windows C drive by doing the following, open a terminal window (Applications->Accessories->Terminal) then type:

```
wine setup.exe
```

where setup.exe is the install file.

N.B. you need to point to the install file with the full path relative to your current location in the directory tree. Either navigate to the directory the installation file is located under, using the cd command, or use a full path in the file specification.

If the installation succeeds (sadly not all apps can be installed under wine, you just have to hope you are lucky) the applications can be launched from the wine menu entries.

Hope that helps

---

