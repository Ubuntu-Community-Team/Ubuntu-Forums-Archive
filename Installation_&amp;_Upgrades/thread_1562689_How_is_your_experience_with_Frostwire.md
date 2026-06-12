---
title: "How is your experience with Frostwire?"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by Extol11 on 2010-08-27
I'm thinking about installing Frostwire again in my Linux hard drive. However, I remember having the same problem all of the time... Frostwire would not close. I selected quit and i'd just minimize. In the best of cases the application would close but it'd still take a space in the bottom bar and I'd have to go to console and kill it manually. So are there any people that downloaded frostwire from the website and installed it that can tell me if it is still having this problem? Maybe I should go with OpenJDK instead of the regular Java? I know this happens in the 64 bit installation only, which is the one I use. Your help is greatly appreciated. Thanks!

---

### Post by proggy on 2010-08-28
still does`nt want to close

---

### Post by Herman on 2010-08-28
:D I don't use Frostwire myself, but I know a few people who like to use Frostwire. 
When they close the program by going 'File','Close', or by clicking the X in the corner of the Frostwire window, it causes the Window to disappear but the Frostwire icon will still be showing up on the right-hand side of the top panel. 
Many people think they have successfully quit Frostwire, but then clicking on the icon brings the Frostwire Window back up again and the program hasn't really been closed, but has still been running in the background, only the Window for it was closed.
For some people on an internet account with restricted bandwidth this can be a nasty problem because they may not have been aware that Frostwire has still been running, and it can silently eat up a lot of bandwidth.
To quit Frostwire, you need to go to the Frostwire icon on the top panel and right-click on it and click 'exit', and then Frostwire will close down. :D

---

### Post by Herman on 2010-08-28
:) Many ISPs offer internet accounts with a bandwidth usage allowance  for normal time plus another allowance for usage during 'off peak'  hours, (like between about midnight and eight am when there are not as  many other users on line).

It's easy in Ubuntu to set programs  like file sharing programs to be started and stopped at certain times of  the day and there are several ways you can do that.
A command line way is to use something called 'crontab', The Official Ubuntu Wiki has a good page on cron, if you want to learn to use crontab you should read that as well, [CronHowto]("https://help.ubuntu.com/community/CronHowto").

If  you would prefer to use a nice GUI program and do the same thing, you  should try setting yourself an appointment in Evolution Calendar, and when you are editing your alarm, don't bother too much with the 'pop up an alert', or 'play a sound' options, go for the 'run a program' option instead.
You  can set Evolution Calendar to open a file sharing program like  bitorrent or frostwire every morning at midnight or two am or whatever,  and you can set another appointment to kill your file sharing program at  eight am or whatever time you like. 

That way you can optimize the use of your internet bandwidth allowance by setting your computer to use it while you're asleep. :)

---

### Post by howefield on 2010-08-28
> **Extol11 said:**
> Frostwire would not close.

The default behaviour is to minimise to tray.

There is an option that allows you to select how Frostwire closes (or minimises). Have you checked out Tools > Options > System Tray and set as required ?

> Maybe I should go with OpenJDK instead of the regular Java?

The currrent version 4.20.9 uses OpenJDK.

---

### Post by Extol11 on 2010-08-29
Thank you guys for all the help. I'll check out those options and that Evolution stuff sounds cool. I had always avoided it because I did not understand it. But now I'll give it a try. Do you have to install any KDE stuff to use it?

---

### Post by Herman on 2010-08-30
> Do you have to install any KDE stuff to use it? 	
:D Quote:
["Evolution]("http://projects.gnome.org/evolution/") provides integrated mail, addressbook and calendaring functionality to users of [the GNOME desktop]("http://gnome.org/").", so , no, you won't need to install KDE. 

Even if you aren't ready to make Evolution Email your default Email program, (although I highly recommend everyone should do so ASAP), you should at least configure Evolution in order to get the full Ubuntu experience. Evolution is an integral program in Ubuntu, and it's really worth the effort and time to try it out and get to know it, at least a little.

I wrote some info about Evolution here: [Configure Evolution Email]("http://members.iinet.net.au/%7Eherman546/p5.html#Configure_Evolution_Email") in case it's any help to anyone. 
Once emails are downloaded, it is not easy to transfer emails and other settings with unsupported operating systems, however, since email may contain viruses, you are much better off using Ubuntu to receive all of your email. You can configure it not to delete the mail from the server if you don't want it to be your default account yet. 
In fact, you can configure Evolution and disable the email account until some stage in the future when you feel ready to make the switch, and still try out the rest of the neat features Evolution has to offer. :D

---

