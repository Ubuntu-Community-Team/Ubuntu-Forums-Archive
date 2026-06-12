---
title: "Need some Remastersys guidance"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by CharlotteThe57th on 2010-05-19
I found the screen shot guide at:

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

useful, but I think the screen shots that show how to  transfer username folders to the skel folder are not easy to understand  what is being done or which folders to choose and which not to, the  actual screen shots are limited in what they show is taking place or I  would need to do.

I want to transfer all my Fire Fox settings/extensions/search engines to  a LiveCd Dist. Do I just transfer my Mozilla folder to skel and nothing  more? 

Plus I want to ensure my LiveCd Dist includes a Desktop folder and it's  content 

These  is these are the most critical steps, more than two screen shots  are needed and there need to be ones that show all the copied username  folders residing in the skel folder. To help I am attaching a copy of  the two screenshots. 

Though in summary I do prefer screen shot guides rather that pithy text  explanations that assume newbies like me understand terminology.


> **aysiu said:**
> <b>For New Users:</b><br />
<a href="http://www.psychocats.net/ubuntu/" target="_blank">The  Psychocats site</a> is a great site for new users to explore. It  uses a combination of terminal commands and screenshot-heavy  point-and-click tutorials to help get you up and running with Ubuntu,  and it addresses many common questions and problems newcomers have when  starting with Ubuntu.<br />
<br />
Psychocats isn't intended to compete with other documentation sites. Its  goal is to give a uniform look and feel for several key tutorials and,  more importantly, not to overwhelm or confuse new users with too many  tutorials in hard-to-find places. Each tutorial addresses a common  Ubuntu question, and all the internal links are on the sidebar.<br  />
<br />
If you're interested in a more comprehensive set of tutorials,  especially ones aimed at advanced or intermediate use (or just anything  not covered on my site--for example, how to use  <i>ndiswrapper</i>), you may want to check out <a  href="http://ubuntuforums.org/forumdisplay.php?f=100"  target="_blank">the Tutorials &amp; Tips section of these  forums,</a> or <a href="https://help.ubuntu.com/community"  target="_blank">the official community-maintained  documentation</a>.<br />
<br />
<b>For Other Users:</b><br />
Thank you for all your help so far!<br />
<br />
Users on these forums have caught typos and other errors and kept me  abreast of changes in versions of software I don't use (e.g. Songbird).  Some users have even contributed whole paragraphs to the Psychocats  tutorials, and I've tried to credit them appropriately.<br />
<br />
<b>Working with Psychocats:</b><br />
I've had numerous requests asking if people can link to or translate the  Psychocats Ubuntu website. The answer is <i>yes</i>. You  can link to Psychocats without asking my permission. If you want to  translate Psychocats Ubuntu, you may do that as well (please let me  know, though--I'm just curious to know what's going on), and I encourage  spreading the knowledge. I haven't officially licensed the  documentation, but the closest I've found to what I'd say embodies the  spirit with which I'm giving Psychocats Ubuntu to the community is <a  href="http://creativecommons.org/licenses/by-nc-sa/3.0/"  target="_blank">the Creative Commons  Attribution-NonCommercial-ShareAlike 3.0 license </a>. If you  would like to mirror Psychocats, you may do so, but please send me a  link to the mirrored site, so I can know to refer people there  also.<br />
<br />
<b>Future Updates and Feedback:</b><br />
If you have any constructive criticism, please leave it in this thread.  I'll be checking back from time to time. I devote a lot of time to the  Ubuntu community and to these forums, especially, but this is not my  main job. So go ahead and leave any suggestions you may have, but I may  not get around to implementing them right away (or at all, depending on  how good the suggestion is).<br />
<br />
If the Psychocats website has helped you, you can post that here, too.  It's always good to know what people have found helpful, and which pages  are most frequently used by people.<br />
<br />
t people have found helpful, and which pages are most frequently used by  people.[/QUOTE]

---

### Post by aysiu on 2010-05-19
/home/*username*/.mozilla contains all your Firefox stuff (passwords, history, extensions, bookmarks).

And, no, you don't have to put in an empty Desktop folder. A desktop folder will be created by default.

---

### Post by CharlotteThe57th on 2010-05-19
> **aysiu said:**
> /home/*username*/.mozilla contains all your Firefox stuff (passwords, history, extensions, bookmarks).

And, no, you don't have to put in an empty Desktop folder. A desktop folder will be created by default.

Thanks, will give it a whirl.:)

With regard the Desktop, I currently have a folder (with very important content) located there and I want to ensure it is transferred to the LiveCd Dist, do I just follow the same method as for the .mozilla folder?

---

### Post by aysiu on 2010-05-19
> **CharlotteThe57th said:**
> Thanks, will give it a whirl.:)

With regard the Desktop, I currently have a folder (with very important content) located there and I want to ensure it is transferred to the LiveCd Dist, do I just follow the same method as for the .mozilla folder?
If your Desktop folder is *not* empty, you should copy it over to /etc/skel

Just remember to *chown* everything in /etc/skel to root before running Remastersys

---

### Post by CharlotteThe57th on 2010-05-19
> **aysiu said:**
> If your Desktop folder is *not* empty, you should copy it over to /etc/skel

Just remember to *chown* everything in /etc/skel to root before running Remastersys

 chown?  Ah I thought it was too easy, command line stuff is something I find a struggle to understand. Is it possible to chown a complete folder inside skel or can I just chown the whole of the skel folder?  Could you help by showing what command line code I would need to enter? Does anything need to be done to ensure full read and write access?

---

### Post by aysiu on 2010-05-19
I think if you use ```
gksudo nautilus
``` to copy your folders to /etc/skel they'll automatically be owned by root.

To be safe, though, when you're done copying everything over, you can paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R root:root /etc/skel
```

---

### Post by CharlotteThe57th on 2010-05-19
> **aysiu said:**
> I think if you use ```
gksudo nautilus
``` to copy your folders to /etc/skel they'll automatically be owned by root.

To be safe, though, when you're done copying everything over, you can paste this command into [the terminal]("http://www.psychocats.net/ubuntu/terminal"): ```
sudo chown -R root:root /etc/skel
```

 Thanks, if I can manage to figure things out and all goes well, I will have the LiveCd/USB I need.

---

### Post by CharlotteThe57th on 2010-05-19
I have managed to create live cd/usb that retains all the settings and  desktop items, my placing things in the skel folder. 

My earlier errors seem to stem from not accessing my username folder  under root as well as with root access to the skel folder.

Thanks to all who helped me learn this solution to what I hope will be a  powerful tool in sharing my custom iso's with others.

The guide on [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) was  particularly helpful and all those who gave tips on this forum:

[http://ubuntuforums.org/showthread.php?t=1487500](http://ubuntuforums.org/showthread.php?t=1487500)
[http://ubuntuforums.org/showthread.php?t=1479155](http://ubuntuforums.org/showthread.php?t=1479155)

Of course one has to thank the developer of Remastersys for creating  something that newbies like me can work with.

---

