---
title: "apt-get install courier problem"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by quartzeye on 2007-03-06
Sorry for reposting:
 
I too am having apt-get problems when trying to install Courier however I am far from knowing how to fix this. The instructions that everyone says works might as well be in in Greek as I am not linux savvy.
 
I was following the instructions on HowToForge for the perfect 6.10 setup in an effort to get a LAMP server running. I followed the instructions to the letter, with only a minor issue here and there until I hit section "13 Courier-IMAP/Courier-POP3". Looks like I would be setting up a secure mail server and client but not sure. The instructions say to do this so and I am no one to question it.
 
Now I am having the same problem others are having but I do not understand how to fix this problem.
 
The instructions say:
 
1. backup /var/lib/dpkg/status to a safe location
Where might a safe location be? I assume that I type in something like:
backup /var/lib/dpkg/status /etc/myfolder/backups
Do I need to make a directory someplace to backup to? Is /etc/... safe?
 
2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w) 
How exactly do I remove all the entries? Do I just do the Unix version of 
del *.* in the folder? Do I use apt-get to uninstall? What exactly do I type in? 
Also what does "nano it" mean? Isn't nano a text editor? Why would I want to edit
files I should be deleting? "search=ctrl-w" is that a nano command to search for
files in the folder? Why not do the Unix equivilent of dir in the folder to list all the
files? I assume it should be empty once you delete or uninstall the entries.
 
3. sudo apt-get upgrade
This I understand.
 
4. sudo apt-get install courier-imap 
This I understand as well but won't this try to reinstall from the same location? Isn't t
that the root problem here, missing 6.10 files in the repositories??? If it works then
great. If someone can explain steps 1 and 2 for the Unix illiterate like my self then I
good with steps 3 and 4. Remember tal slowly and assume that I barely know where
the power switch is for the PC. That way nothing is left to question as no assumed
knowledge is present on my part.
 
Thank in advance
Quartzeye

---

### Post by quartzeye on 2007-03-07
I do not know how it worked but I went back through and verified the repositories and reran "apt-get update" and "apt-get upgrade".  The system updated again but his time when I went to run the "apt-get install courier" packages they installed without a problem.

Now mind you I did not change anything other than running the basic update and upgrade commands again.  So things fixing themselves without me doing anything always makes me nervious but I am not going to look a gift horse in the mouth.

I did read over on HowToforge, and other places, a comment or two suggesting that atleast the "apt-get upgrade" command must be ran more than once.  Does this seem correct?  It obviously did something for me but 24 hours later changes could have been made to the package repositories and I would not have known any different.

Quartzeye

---

