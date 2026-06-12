---
title: "Anyone installed DB2 Express C?"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by timka1 on 2006-09-11
I read that Ubuntu are certified by IBM for DB2 so I was surprised that there was nothing found for "DB2" when I searched in the How To forum or even in this one.

Anyhow late Saturday night I downloaded db2exc_91_LNX_x86.tar.gz (200+ MB) from the IBM site and extracted the "exp" folder into the Desktop.

I noticed that there were three shell scripts in sub folder "disk1": db2_install, db2setup & installFixPack

(effectively I had typed "[COLOR="Red"]cd ~/Desktop/exp/disk1[/COLOR]")

Fingers crossed I typed: "[COLOR="Red"]sudo sh db2_install[/COLOR]" and after a lot of activity it completed without a hitch.

Next I typed "[COLOR="Red"]sudo sh db2setup[/COLOR]" and again the install gods were with me and this time a gui sprang to life and I took the "Install a Product" option and I just took the defaults.

Again everything looked good (I can post logs if there is anyone who needs to see)

Next I typed "[COLOR="Red"]sudo sh installFixPack[/COLOR]" and it errors with "DB2 installer detects that one or more DB2 instances are still active. Stop the active instances and rerun the command again"

Now I'm wondering: do I actually need to run "installFixPack"?

If I do, how do I control the DB2 instances?

More generally all the IBM tutorials seem to assume a command line interface (CLI) but when I type the commands mentioned I just get "bash command not found". How do I get into this DB2 environment?

I suspect that there is a way to get into a gui that shows the DB2 status and other goodies but I don't know how to get there.

Hopefully someone out there has done this...

---

### Post by luv2craftca on 2006-09-11
I will be trying to install this sometime this week  for a course I am taking.... I found this HOWTO on the web.  

I don't know if it is accurate or useful but it might help.

[http://www.tldp.org/HOWTO/DB2-HOWTO/introduction.html](http://www.tldp.org/HOWTO/DB2-HOWTO/introduction.html)

luv2craftca

---

### Post by timka1 on 2006-09-12
Thanks luv2craftca: looks useful but it does state DB2 Express version 8.2 whereas download is now at 9.1.

I'm not at my Ubuntu machine for a few hours so I won't have a chance to try it out.

Assuming we manage to do it it would be great to feedback a HowTo for Ubuntu users. For the moment I'll post back progress on this thread. As I said before I'm just surprised that a HowTo didn't come out of the IBM accreditation process.

---

### Post by timka1 on 2006-09-13
OK this what I found out so far:

The [www.tldp.org](www.tldp.org) document referred to above is a bit out of date, specifically the default user names and group names have changed.

I found that most of the install had worked when I tried some of the suggested changes and you'd be better off not following the instructions. I think the only thing I found was you need to check that the groups contain the relevant user using menu option *System>Administration>Users and Groups*. 

But this link on the IBM forum sorted out everything:

[http://www-128.ibm.com/developerworks/forums/dw_thread.jsp?message=13861079&cat=28&thread=132776&treeDisplayType=threadmode1&forum=913#13861079]("http://www-128.ibm.com/developerworks/forums/dw_thread.jsp?message=13861079&cat=28&thread=132776&treeDisplayType=threadmode1&forum=913#13861079")

I reckon that I have enough to make a basic HowTo which would have helped me anyhow...

---

### Post by luv2craftca on 2006-09-15
Thanks for the link timka1.  I will definately read through that prior to my install of DB2 (delayed until this weekend).

---

### Post by stansaraczewski on 2006-12-12
Where can I download db/2 from ? I've roamed around searching - but cannot find where to download it from... 

[WWW.IBM.COM](WWW.IBM.COM) only seems to have trial versions. Anyone have a url ?

Thank You -

---

### Post by stansaraczewski on 2006-12-13
Found it - installed it - and got it working.

---

### Post by jigr69 on 2007-05-04
I've recently installed Ubuntu in order to get a LAMP environment as well as letting the kids play with a new desktop.  However decided to explore the use of DB2 at work, on the newly created server at home.

Downloaded and installed DB2 Express C after some searching around. Managed to get the db2sampl script running to connected to the database and completed a SELECT statement. 

The bit I'm having trouble with is getting the control center to run, keep getting errors such as

java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:190)
        at java.awt.Window.<init>(Window.java:344)
        at java.awt.Frame.<init>(Frame.java:452)
        at java.awt.Frame.<init>(Frame.java:417)
        at javax.swing.JFrame.<init>(JFrame.java:180)
        at CC.createDummyNavigatorFrame(Unknown Source)
        at CC.initialize(Unknown Source)
        at CC.construct(Unknown Source)
        at CC.<init>(Unknown Source)
        at CC.main(Unknown Source)

I've tried issuing the commands xhost -localhost but to no avail. Anyone help?

Cheers

---

### Post by jigr69 on 2007-05-05
It was late when I posted this, managed to get db2cc started and running. Now the fun begins!

---

### Post by javahollic on 2008-04-12
Mmm, I have some systems running at work (gutsy->heron), at home, I just get:

SQL1220N  The database manager shared memory set cannot be allocated.

to be fixed...:(

---

