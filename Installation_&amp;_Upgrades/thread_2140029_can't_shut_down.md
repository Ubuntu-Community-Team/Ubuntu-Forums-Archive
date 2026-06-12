---
title: "can't shut down"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by Juan Felipe Bertrand on 2013-04-28
I just installed 32- bit Ubuntu 13.04.  When I click on shutdown, the system reboots.  How can I get the computer to turn off?

Sometimes it has shut down properly, but most often, it goes back to the grub-2 screen.  I will then select Windows 7, let it boot up, then shut down to get my laptop turned off.

Should I try to reinstall again?  It doesn't seem to help.  I've tried many of the suggestions on the various forums.  Most of them talk about editing the grub-2 script; some others talk about various terminal commands.  I've also read that linux in general shouldn't be shut down.  Maybe that's the problem.

---

### Post by Juan Felipe Bertrand on 2013-05-07
Well:p I think the problem is solved.  Here's what I read on askubuntu.com; and I tried this solution.  It actually worked fine immediately upon shutting down the computer  FYI I also have a new Acer Aspire V5 notebook.  



[TABLE]
[TR]
[TD="class: votecell"]     1     down vote         
              [/TD]
                [TD="class: answercell"]     I had the same issue with new acer aspre v5 notebook. It has been solved by enabling laptop-mode as running 
  sudo apt-get install laptop-mode-tools.
  Hope it will help you.
 
     [TABLE="class: fw"]
     [TR]
     [TD="class: vt"]          [share]("http://askubuntu.com/a/178787")[improve this answer]("http://askubuntu.com/posts/178787/edit")
                    [/TD]
     [TD="class: post-signature, align: right"]                                             edited                              [Aug 22 '12 at 2:19]("http://askubuntu.com/posts/178787/revisions")          
                      [URL="http://askubuntu.com/users/1992/rolandixor"][IMG]http://www.gravatar.com/avatar/d629b6ac45d58dbd918c0246b364748d?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [RolandiXor]("http://askubuntu.com/users/1992/rolandixor")&#9830;
            34.4k864143         
     
     [/TD]
                    [TD="class: post-signature, align: right"]                                                                     answered  Aug 22 '12 at 0:49         
                      [URL="http://askubuntu.com/users/84787/erichuang"][IMG]http://www.gravatar.com/avatar/4022602865c4bbb623710ae3bc0bd264?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [erichuang]("http://askubuntu.com/users/84787/erichuang")
            111         
     
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

