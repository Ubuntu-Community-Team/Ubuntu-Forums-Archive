---
title: "Help to back up his application data"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by markling on 2008-11-27
Hello

Need to backup my application data. But I've not idea where it is. Nor which files I would need to copy, nor how I would go about restoring them.

I've searched help topics far and wide to no avail. Some skirt around the subject but presume a certain level of knowledge about the linux command line and directory structure. Is there anyone who can spell it out for me?

Thanks

Markling.

P.S. Ubuntu powers that be - Please Note how regular users fall through the Ubuntu help gap:

I have tried searching first for info on how to backup Skype data. Instead, I discovered a large gap where ignorant users are left in the lurch.

For example, the entry under "Make backup copies of your files" in the local Ubuntu help files contains only cursory information. It suggests using a backup utilitiy. But the utilities I have tried offer no help in locating and copying application data. They presume you know where it is. Surely this is vital? Is Ubuntu really intended to compete with Windows for home users? Or is it an o/s for nerds alone?

If I was only slightly more ignorant than I am about computers I wouldn't even know where to start.

As it is, I know enough to search for "application data settings backup" in the Installation & Upgrade pages of the Ubuntu Forums. This throws up some clues, but are no help to anyone who isn't already in the know.

e.g. These threads come back in the search results:

[http://ubuntuforums.org/showthread.php?t=834832&highlight=application+data+settings+backup](http://ubuntuforums.org/showthread.php?t=834832&highlight=application+data+settings+backup)

[http://ubuntuforums.org/showthread.php?t=849862&highlight=application+data+settings+backup](http://ubuntuforums.org/showthread.php?t=849862&highlight=application+data+settings+backup)

Not the idiot's guide that I need. I suspect that even if I found an idiot's guide, it would require too much faffing about and would discourage regular users enough that they would consider going back (heaven forbid) to Windows. 

Searching for "application data settings backup" in all Ubuntu Forums brings up 121 threads. On the *third* page of search results there is an item ([http://ubuntuforums.org/showthread.php?t=878177&highlight=application+data+settings+backup](http://ubuntuforums.org/showthread.php?t=878177&highlight=application+data+settings+backup)) that, while not providing the idiot's guide I need, does include a link to a guide on another website:

[http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)

This is not an idiots guide either. It does provide some pointers that are of some use to advanced users. But regular users are left at sea. From my own limited knowledge, I can see from here that the application data appears to be stored in hidden folders. Going by the convention used in this guide, I would presume that to find my Skype data, i need to search for ~/.skype. But searching for this finds nothing. Can you imagine a regular user figuring out what ~/. is? Or where the hell to find their Skype data so they can do a simple backup?

How about the Skype website? Skype gives plenty of help for people who want to back up their data in Windows: [http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=413](http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=413)

But nothing that I can find for Linux. Searches throw up yet more Windows advice. Dig far and long enough and you can find a reference to a "Skype Linux FAQ", but the page has been removed: [http://www.skype.com/help/faq/linux.html](http://www.skype.com/help/faq/linux.html)

Google searches don't help. Searches for tutorials of the linux file and directory system are no use. And what regular user would know to search for tutorials of directory structures?

The result is that I'm wasting an awful lot of time just trying to find out some fundamental information so I can protect my data. Are Ubuntu users expected to learn to use the linux command line in order to do something fundamental like backup their data? Do they really have to learn what's going on under the bonnet (hood) just so they can use their computer to run simple utilities for everyday tasks?

---

### Post by cariboo on 2008-11-27
There are plenty of post on how to back up configuration files. To locate the configuration files, go to Places-->Home Folder and press Ctrl-h this will reveal the hidden directories and files.

All the other configuration files are located in /etc. Go to Places-->Home Folder-->Files System.

As an aside you don't have to search for Ubuntu specific solutions only. Most Debian based distributions are largely the same, and generally under the gui most Linux distributions are the same.

> P.S. Ubuntu powers that be - Please Note how regular users fall through the Ubuntu help gap:

I have tried searching first for info on how to backup Skype data. Instead, I discovered a large gap where ignorant users are left in the lurch.


Skype is not supported by Ubuntu, but if you had bothered to ask, I'm sure there would have been many answers to your question. For instance to locate all the Skype files, if you installed using a .deb file go to System-->Aministration-->Synaptic Package Manager, highlight the package and click the Properties buttion, then click the installed files tab.

Jim

---

### Post by markling on 2008-11-28
Thanks cariboo907, that's quite helpful.

> To locate the configuration files, go to Places-->Home Folder and press Ctrl-h this will reveal the hidden directories and files.

So this is why another post I read on the subject said something like "just copy your home folder"?

The only thing is, what are all the files that are listed there? Is it only working application data? or are their other sorts of files as well? In other words, if I just copied my home folder and then copied it back when I wanted to restore from a backup, could there be unforeseen problems like copying old executables onto new? Should I perhaps only copy specific files? If its that easy, then why don't the backup Ubuntu utilities I've tried have a button that says something like 'Backup your application data - one click!"?

I hope you understand the basic issue I'm trying to raise about this. And that's that for regular users, all these directories and jargon and tings don't look pretty.

I looked in the Synaptic Package Manager as you suggested, but I'm none the wiser, aside from having found the location of some Skype files, which I grant is great progress, but still hasn't addressed the fundamental problem a regular user will face when trying to back up their application data.

So you say, "There are plenty of post on how to back up configuration files". But that's not the point. None I could find in a reasonable time-scale were of any help to me as a noddy user.

The whole experience is enough to put your head in a tailspin, when all you want to do is make sure everything's backed up before you upgrade to the latest version of the o/s.

Reading all these posts with command line instructions and looking at all these directories feels like being told to decipher the Rosetta Stone with nothing but English language training. Is it sanskrit? Is it worth the trouble?

> Skype is not supported by Ubuntu, but if you had bothered to ask, I'm sure there would have been many answers to your question. For instance to 

Well, asking was the original reason for my post. But I had an important point to make about my experience as a muppet user trying to find out how to backup his application data. 

Skype is merely an example I've given to demonstrate my point, which is that ya'll could accomodate noddy users a little better. I am working on the assumption that, not being a coder, I'm doing *my* bit for the Ubuntu community by raising this point. Don't shoot the messenger. I'm still not sure about which files I should copy to save my application data and settings. And I've not even thought about applications other than Skype yet. That's just the first one I looked at. At least, with this home directory advice you've given, I'm now in the ballpark. Will someone switch on the floodlights and show me how to hold a bat?

Perhaps there's some sort of way the whole procedure can be made idiot-proof so noddy users don't have to go rooting around under the bonnet (hood)? I presume Ubuntu *is* a windows killer, isn't it, and so suitable for home users, yes?

In that regard, Mozilla have to be commended for the backup facility they released for Thunderbird over the summer. To backup Thunderbird data also used to require rolling up your sleeves and rummaging around blindly in directories that look to the layman very like the spaghetti of pipes under the control panels of the Tardis. Now you just have to select a menu item. It's amazing what you can do with computers nowadays.

cheers

markling.

---

### Post by markling on 2008-12-01
i've still got this little matter of not being able to upgrade to the latest version of ubuntu because i don't know how to backup my application data safely.

---

