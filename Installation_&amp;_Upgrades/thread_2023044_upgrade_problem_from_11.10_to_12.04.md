---
title: "upgrade problem from 11.10 to 12.04"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by hufemj on 2012-07-11
I had an upgrade failure from 11.10 to 12.04. The system comes up with a login screen. The splash screen says 11.10. When I try to login, it looks like it accepts my password and then immediately logs me out.

I tried booting from a LiveCD because another thread indicated there would be a repair upgrade command, but I don't see that. It tells me 12.04 is already installed.

I ran the command suggested in another thread:

sudo dpkg --configure -a 

after logging on to a recovery session and it tells me,

"dpkg: error: parsing file '/var/lib/status' near line 21798 package 'xmind' : blank line in value of field 'Description'"

But, I don't know what to do about it. Edit it with vi and delete the blank line?

---

### Post by hufemj on 2012-07-11
The problem is fixed.

I edited the status file with vim and found a configuration problem with xmind. Blank lines in text should be accomplished with a space and a period: " .", as indicated elsewhere in the file. For whatever reason, paragraphs in the description for xmind were separated with a blank line, which apparently is used to separate packages.

Anyway, I made the edit and executed the following command:

sudo dpkg --configure -a

and was able to resume the process. The same error showed up in an 'available' file and I made the same fix to that. Eventually, the command ran to completion.

Then I did:

sudo apt-get upgrade -f

and

sudo apt-get update

and was pretty much back in business.

Problem solved.

---

