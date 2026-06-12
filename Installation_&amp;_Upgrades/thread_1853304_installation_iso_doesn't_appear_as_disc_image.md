---
title: "installation iso doesn't appear as disc image"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by kitandkaboodle on 2011-10-02
Am trying to create a boot/install CD of 10.4 LTS to install ubuntu on other machines. (I already am working with 10.4 on my current machine.)
Have been following disc-creation instructions at [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).
I succeeded in the first step of downloading an iso onto my ubuntu desktop.
Two problems:
1. The downloaded iso has a good name (ubuntu-10.04.3-desktop-i386.iso) but it appears on my desktop in the form of a drive icon, not a disc icon. But the instruction page shows a disc icon. (I've checked other instruction pages for this as well, and they also show a disc icon.) 
2. The instruction page says to right-click the iso and choose "Write to Disc", but there is no such right-click option on the 10.4 lucid I'm using, even when an empty disc is inserted. (There is no such option for other files, either. Furthermore, even my burning software like Gnomebaker and Brasero aren't even recognizing the iso I've downloaded as being on the desktop.

Questions:
Do I need the iso file icon to appear as a disc rather than a drive? If so, how do I get it that way?
Whether or not I need a disc image icon, is it possible to enable "Write to Disc" as a right-click option?

---

### Post by Quackers on 2011-10-02
The page you are using for instructions has the Windows box highlighted by default. Click on the Ubuntu radio button and then click on "Show me how".

---

### Post by kitandkaboodle on 2011-10-02
I already clicked Ubuntu and "Show me how". If you do that, you'll see the same inconsistencies that I mentioned in my first post.

---

### Post by Quackers on 2011-10-02
I see. Does Brasero find the file?
I don't know why the iso appears as a drive icon.

---

### Post by kitandkaboodle on 2011-10-02
Brasero does not find the file.
The iso file is the download for version 10.4LTS from that same download page. Just to describe more clearly: it's of squarish (drive-type) appearance rather than circular disc appearance.

---

### Post by Quackers on 2011-10-02
Try and cut/paste the file to your Downloads folder and then see if Brasero recognises the file.
The file shouldn't necessary appear as a disc icon. It's just a file of type .iso

---

### Post by kitandkaboodle on 2011-10-02
Per suggestion, tried to move the iso icon to downloads folder but got message saying it was not allowed or possible.
Right-clicking the icon showed also that the "Cut" command was not active for it. One unusual command that was active on right-click was "Unmount", situated where normally is "Send To" or "Eject". Out of curiosity, I clicked "Unmount", and my iso icon promptly disappeared, a search rendering nothing. I appear to have lost my download, for whatever it was worth. It seems that the download may have resulted in some sort of boot drive rather than a disc image. Not sure if worth trying again.

---

### Post by Quackers on 2011-10-02
If the iso was mounted then it is likely that Brasero would not see it.
Where did you download the iso to? Have a look in the Downloads folder and see if it's there.
Now it's unmounted try Brasero again.

---

### Post by kitandkaboodle on 2011-10-02
(BTW thanks very much for suggestions) Tried a search for "i386.iso" and did not turn up that file. Looked in downloads folder, but nothing. The "unmount" command did not indicate any destination. Seems to have vanished. Do you know where nonspecified "unmount" might go?

---

### Post by Quackers on 2011-10-02
I don't even know how it got mounted :-)
If it's not in Downloads try your home folder (your username folder), it may be there. Is your search function set to search the file system or just one folder? Set it to file system search.

---

### Post by kitandkaboodle on 2011-10-02
Not in home folder either. Did search file system.
Hopefully I don't have 700mb of junk unmounted away in some obscure nook.
I don't know how it got mounted either. That's how it appeared after the download was complete.

---

### Post by Quackers on 2011-10-02
Well, for it to have been mounted you must have downloaded it to somewhere :-)
Set the Firefox options to always ask you where to download things to. That way you know where everythings gone.

---

### Post by kitandkaboodle on 2011-10-02
OOps-- spoke too soon. I changed a parameter in the search (noticed it was set to zero days). As you suggested, it yielded the "raw CD"  file in the /tmp folder. Now I've got to brush up on how to get into that....

---

### Post by Quackers on 2011-10-02
That's the one :-)
Change the settings in Firefox to ask you where to download things to, or to always go to the Downloads folder.
I must admit to not knowing how to get to that file now, unless /tmp appears in the navigation menu within Brasero?

---

### Post by jocko on 2011-10-02
> **kitandkaboodle said:**
> Not in home folder either. Did search file system.
Hopefully I don't have 700mb of junk unmounted away in some obscure nook.
I don't know how it got mounted either. That's how it appeared after the download was complete.

> **kitandkaboodle said:**
> OOps-- spoke too soon. I changed a parameter in the search (noticed it was set to zero days). As you suggested, it yielded the "raw CD"  file in the /tmp folder. Now I've got to brush up on how to get into that....

The file probably got mounted because when you clicked the download link you selected "open with" instead of just download. Then the file is downloaded to /tmp and mounted, placing a drive icon on your desktop.

Just browse to /tmp in brasero's "select image" browser (filesystem-->/tmp), or copy the file to your desktop:
```
cp /tmp/*filename* ~/Desktop
```

---

### Post by Quackers on 2011-10-02
That would explain it :-)  Thanks jocko!

---

### Post by kitandkaboodle on 2011-10-02
So far so good. Brasero can find tmp file in "file system". Am burning as I write. One drawback, Brasero options allow write speed of minimum 10x, higher than recommended. But this is close enough for a try. 
Cheers, Quackers, and thanks for tips.

---

### Post by Quackers on 2011-10-02
Hmm, check the md5sum of the iso file after

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or at least check the disc for errors. Boot from the disc and at the first purple screen press any key. Then choose your language and on the next screen select "check for errors". If any errors are found the disc is no good.

---

