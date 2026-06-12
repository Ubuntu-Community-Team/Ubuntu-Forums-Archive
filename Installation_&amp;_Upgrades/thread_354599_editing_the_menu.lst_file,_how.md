---
title: "editing the menu.lst file, how?"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by drumkitcat on 2007-02-06
Hi,

I've installed Xubuntu and I'm getting the following when I try to boot:

BusyBox
/bin/sh: can't access tty; job control turned off
(initramfs)

- what am I supposed to do here? I typed ls and got a short list of available commands or words, but I don't know what's happening (totally new to Linux/Unix) 

I searched these forums, and found that there's some way you can tell something to look somewhere else for the hard drive... but that you have to edit the menu.lst file once you get into xubuntu...

How do I do that?  Everyone talks about a terminal, but not being able to even get past the text screen listed above, I don't know how to fix that.

This is the 4th time I've installed Xubuntu on the system, and this is happening with the Alternate CD Version disc - which did check out just fine when I verified it, and burned at 4x speed... it installs perfectly, but I need to change the pointer to boot from the right place... just need to know how..

Help please!
thanks
Paul

---

### Post by coffeecat on 2007-02-06
Don't go editing menu.lst - this is the text menu that controls the Grub bootloader. This is not a Grub problem.

I've just done a quick forum search with 'busy box /bin/sh can't access tty' as the keywords and it seems that you are not the only one getting this problem with Edgy (version 6.10). I don't have a solution, but I do have two suggestions. Since you are new to *buntu, download the CD image for Dapper (version 6.06). Other people with this problem weren't having it with Dapper, and Dapper is a perfectly good version of the distro for you to begin with. Because of a number of persisting issues (=bugs :wink: ) with Edgy (which had a very short development cycle), I still prefer to use Dapper for which updates will continue to be available for another two years or more - or so I believe.

Suggestion 2 - search the forums/google for 'Busy Box'. That might give you some leads.

By the way, as a Linux newcomer you may not know about [www.google.com/linux](www.google.com/linux) (or [www.google.co.uk/linux](www.google.co.uk/linux) in the UK). Very useful.

---

### Post by drumkitcat on 2007-02-06
Thanks very much for the insightful reply! 
I really appreciate it!

I will check out those links, as well as downloading the Dapper version

(note, I did try the live cd version of dapper on that particular computer to begin with and it hung up, but I will try the Alternate CD version of it and see if that will work instead)

thanks again!

Paul

---

