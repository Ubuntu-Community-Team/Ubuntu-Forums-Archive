---
title: "Upgraded Hardy to Intrepid"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tonyds_ on 2008-10-13
Personally, my upgrade (I used update-manager) went very well and the system feels more repsonsive too.  Just two issues.  

First, the network manager is gone all together from my panel and I can't find it in the list to add.  I also don't know how to install it... ?

Second, the upgrade utitlity got rid of my PDF printer.  I think I solved that by installing the cups pdf package but I'm not at my computer right now and forgot to test that.

Great work again by the Ubuntu team.

---

### Post by ubuuntu9897 on 2008-10-13
good i may want to use it 8.04 hasnt been the best personaly for me

---

### Post by randy78 on 2008-10-13
Intrepid is Beta, and the network manager won't be available until either the release candidate or the final release (from the release notes)

Just remember that the beta is for testing only, and not meant for production (regular use) machines. You should read the release notes, at the very least, to get a better understanding of what was left out, what bugs there are and all that.

Good Luck

---

### Post by Piraja on 2008-10-14
I have been so pleased with Intrepid on my laptop I decided yesterday to upgrade also my desktop PC from Hardy to Intrepid. (My main "production machine" is still at the office, so I'm not afraid to test things at home.) Well, this time it was not such a big success — lots of bug reporting to do and things to figure out. 

I found this thread by searching UF for **cups-pdf** related posts. I knew that I would have to tweak printing settings, since I was warned about the changes concerning them during the upgrade process.

So I had to install **cups-pdf**. No problem. However, one thing really puzzles me — the fact that I cannot find the output files! Here are the lines I think that are relevant in the **/etc/cups/cups-pdf.conf** file: 

```
### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out ${HOME}/PDF
```

Now I tried changing "HOME" to "USER" but I still cannot locate the PDF files I just printed. They are not in my home directory. I checked quite a few other places too, including root home directory. They must be somewhere, because everything seems to work normally: the document is shown in the Document Print Status dialog and then disappears just as it should — or if I choose to show completed jobs, they are listed as "Completed". And the ink-jet prints just fine.

Strange!

---

### Post by Piraja on 2008-10-14
If I used smilies, I would put a blushing red face here...

All I had to do was (in addition to doing some googling and forum-searching) to change the ownership and permissions of the backend directory and file cups-pdf therein:

```
cd /usr/lib/cups/backend
sudo chown root:root cups-pdf
sudo chmod 700 cups-pdf
```

I think I may have messed up the file and folder permissions previously, so I'm not sure if even this really has to be done.

After this it was easy to add the CUPS-PDF printer in System > Administration > Printing.

There is an obsolete thread on CUPS-PDF; see [# 141 on its page 15]("http://ubuntuforums.org/showthread.php?t=188860&page=15") before reading the rest.

---

### Post by saltydog on 2008-10-26
With Intrepid you don't need anymore cups-pdf. Just hit "Print to file" in the print dialog and give it a pdf extension.

---

