---
title: "I am not sure, clean re install + same /home"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2007-10-20
Gutsy is out, and it does sound like it is a good improvement from feisty. 

I'd like to install it doing a clean install, and get rid of my feisty, the problem is that I would my files and configurations.

So, My plan is to copy all the contents of /home to some auxiliar disk (I do not have a separate /home partition) Then copy them again to the new /home , this would be a good opportunity to increase the size of the partitions used by ubuntu cause right now my brother is the only windows user on this computer and I'd like to use the harddrive I own entirely on ubuntu so this requires some reformat...

The question is whether this will actually work, on the other hand, can I use my current feisty partition as an extra disk and just install gutsy somewhere else?

---

### Post by Herman on 2007-10-20
Short answwer is 'Yup!' :)

Long answer is, 
I have done that many times and I have never had any problems with it. It's okay to copy the entire /home directory if it saves you tims, but I don't restore my entire /home/herman directory in case there's any files in there that will overwrite any software related files that are improved to match the software in the new release.  
I only copy out the files I need, like firefox bookmarks, evolution addressbook, calendar, mail, memos and tasks.
Also I use Password manager, so I  save the file for that as well, and copy that into my new install. 
If you use other added software that might have related files on your /home directory for storing your personal settings, make sure you find those and copy them across too.

Even longer answer is here: [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm")

As for installed software itself, I always install that again through Add/Remove programs or Synaptic or aptitude, so it will match the new operating system. 
If you have a list of the software you like to install (it could be a good idea to make one), it wouldn't be much more work to make your own software installation script and run it if you're keen enough.  That would speed things up a lot. 

Regards, Herman :)

---

