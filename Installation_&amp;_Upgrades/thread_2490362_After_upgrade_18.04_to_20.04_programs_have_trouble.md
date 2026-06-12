---
title: "After upgrade 18.04 to 20.04 programs have trouble monitoring filesystem updates"
date: 2023-08-31
forum: Installation &amp; Upgrades
---

### Post by vicmortelmans on 2023-08-31
Hi,

I upgraded from 18.04 LTS to 20.04 LTS. The upgrade went very smooth, but I have a new problem with two applications, that may seem to have a single root cause. 

Digikam and neomutt both fail to keep in sync with external changes to the filesystem.

E.g. when I create a new directory (album) while Digikam is running, it won't show up in the album view. Even refreshing the view won't work. After restarting the program, the new directory shows up.

E.g. when I send a mail in neomutt (and also on some other conditions, I didn't pin down when exactly), duplicate entries are shown in the list view, one of which cannot be opened, with a file not found error. After restarting neomutt, everything is OK.

Can this be related to the upgrade? I've been looking for a solution. Maybe I'm not looking for the right search terms, but I'm not getting any further...

Thanks for having a look!

Best regards,
Vic

PS. here's my filesystem layout, if that's of any help:

[IMG]https://i.imgur.com/OMGMTkM.png[/IMG]

---

### Post by TheFu on 2023-09-02
Don't see what file systems or disk layout has to do with programs not refreshing.
Start simple.  Use the CLI - are the new files there or not?  
If they are, check using a GUI file manager. Are the new files there or not?
If they are, you've just figured out that the problem it in the photo program.  Find their project page and file a bug report.

And always look at the system logs for any warnings or errors, track those down and correct as many as you can.  Just take the error and put it into a search engine. Best to remove any timestamps or system specific things from that search.  May need to review 2-5 articles to find one that applies.

Images are bandwidth hogs. Please use text when possible.  **parted -l** would show the same information ... or **lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint** would show more information.  When posting text from the terminal, please, please, wrap that output in forum 'code' tags so the columns line up with the headers and it is easy to read. No other formatting does that in these forums, except 'code tags'.

---

