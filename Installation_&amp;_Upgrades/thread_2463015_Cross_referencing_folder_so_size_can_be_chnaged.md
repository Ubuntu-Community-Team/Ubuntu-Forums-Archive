---
title: "Cross referencing folder so size can be chnaged"
date: 2021-06-01
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-01
Example 
I have a folder - file manger tells me "LIBRARY".
The "properties " tells me the partition size.

**That is all I know about it . NO location properties. **

I want to change the size. 

So I click "Open in Disks" 

Disks open and I get 
" No disk selected" or something like that. 

At this point I have no idea WHERE "LIBRARY" actually resides. 

[B]Is there a way to accomplish the task of changing the size of "LIBRARY ' in Ubuntu 
using GUI ? 
[/B]

---

### Post by SeijiSensei on 2021-06-01
If the partition is mounted, the command **df** will tell you where it's mounted. Just focus on the /dev/sdX entries. The rest of the entries aren't pertinent to your question. Another option is to run "sudo fdisk -l" which will provide a census of all the block devices in your system.

I wouldn't try to do any of this from a GUI. It's so much faster from the command prompt.

---

### Post by anneranch on 2021-06-01
> **SeijiSensei said:**
> If the partition is mounted, the command **df** will tell you where it's mounted. Just focus on the /dev/sdX entries. The rest of the entries aren't pertinent to your question. Another option is to run "sudo fdisk -l" which will provide a census of all the block devices in your system.

I wouldn't try to do any of this from a GUI. It's so much faster from the command prompt.

What you are indirectly saying file manager (GUI)  button to open "Disks" (GUI) is worthless "feature". 
Also I am not after ALL  block devices , I just want to identify the partition and resize it. 
Speed is immaterial, finding the partition IS.

I guess my expectations are little too high. 

CASE CLOSED

---

### Post by scorp123 on 2021-06-02
> **anneranch said:**
> What you are indirectly saying file manager (GUI)  button to open "Disks" (GUI) is worthless "feature". 

No, what he was saying is that what you wrote up there was too vague. If you are talking about GUI stuff you could at least have posted some screenshots maybe? We don't have crystal balls, we can't see what you see. There could be a million reasons (e.g. OS is installed in a different language?) why we can't immediately comprehend what you mean.

Resorting to text commands has the advantage that those commands are universally valid, e.g. it does not matter what language we or you use - the command will work and produce output that can be analysed. Also copying + pasting text is perhaps easier than working with screenshots.

Try to see it this way. We can't help you if you don't provide precise information.

---

### Post by anneranch on 2021-06-07
> **scorp123 said:**
> No, what he was saying is that what you wrote up there was too vague. If you are talking about GUI stuff you could at least have posted some screenshots maybe? We don't have crystal balls, we can't see what you see. There could be a million reasons (e.g. OS is installed in a different language?) why we can't immediately comprehend what you mean.

Resorting to text commands has the advantage that those commands are universally valid, e.g. it does not matter what language we or you use - the command will work and produce output that can be analysed. Also copying + pasting text is perhaps easier than working with screenshots.

Try to see it this way. We can't help you if you don't provide precise information

Did you actually read the original post ?

---

### Post by deadflowr on 2021-06-07
Where is Library showing in the file manager?
Note that there is no such directory called Library in Ubuntu, so it's either a directory you created or it's a directory or something mounted from elsewhere like a network share.
Are you accessing network shares?

---

### Post by SeijiSensei on 2021-06-07
Humor me and open a terminal with Ctrl+Alt+T, then run "df". What do you see?

---

### Post by ajgreeny on 2021-06-07
> **anneranch said:**
> Example 
I have a folder - file manger tells me "LIBRARY".
The "properties " tells me the partition size.

**That is all I know about it . NO location properties. **

I want to change the size. 

So I click "Open in Disks" 

Disks open and I get 
" No disk selected" or something like that. 

At this point I have no idea WHERE "LIBRARY" actually resides. 

[B]Is there a way to accomplish the task of changing the size of "LIBRARY ' in Ubuntu 
using GUI ? 
[/B]
If **LIBRARY** really is a folder, as you have called it, you can not change its size either by GUI of by command line; a folder is simply that, a folder or named place in which you can place files or subfolders and its size will be dependent on what it contains.  
If I use a right click on an empty folder in my file manager and view Properties I see in the Size box "**1 Item, totalling 0 bytes**"; in the file manager size column it shows as 4KiB.

From all of this I think you may be confusing files, folders and partitions; what we need to be sure of is which of those your LIBRARY actually is.

If it is a partition you may be able to change its size but we do need to know exactly what we are dealing with here.
What do you see if you left double click on the LIBRARY, or single click if you see it in the left hand pane of your file manager?  Does it open and show anything?

The output from that ***df*** command may indeed be very useful so please show us that as soon as possible.

---

### Post by SeijiSensei on 2021-06-09
It could be a device with "LIBRARY" as its label.

---

### Post by rsteinmetz70112 on 2021-06-09
If it is a folder the full path would be useful. 
The OP does seems a little touchy though.

Folders is not an especially *nix term. Mostly they'er called directories. They contain files (virtually everything in *nix acts like a file). They will grow as more files are added to them, until the device (usually a partition) is full, you normally do not need to increase the size of a directory. 
Partitions are mounted onto a filesystem at a mount point, so the full path is needed to determine which partition any directory is located in. The df command (among others) will give you that information.

---

### Post by scorp123 on 2021-06-09
> **anneranch said:**
> Did you actually read the original post ?

Yes, and it didn't make much sense. There is no location named "LIBRARY" out of the box. Whatever that is you see there, none of us here can tell what it could be or where that came from. Try posting screenshots maybe? Or try the terminal commands you were already given. 

I don't do Tarot cards or crystal balls. So if you don't want to provide more useful information...? Fine I guess. It's your computer. Have a nice day.

---

