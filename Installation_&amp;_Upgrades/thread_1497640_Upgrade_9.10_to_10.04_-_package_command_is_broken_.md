---
title: "Upgrade 9.10 to 10.04 - package command is broken (mailagent?)"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by KermEd on 2010-05-30
Hello everyone,

I've only been using Linux for a few days (Specifically - I installed Ubuntu 9.10 last week on my laptop for learning the OS and updated to 10.04 over the weekend).  I have searched Google (and found answers) for every problem now except for this new one.  I apologise in advance for the length but I wanted to include my own troubleshooting as well.

When I installed and setup Ubuntu Karmic - I added my work software.  Autopackage wasn't installed by default so I used terminal's package install <filename> command for the first file - and double clicked on the rest to install.

With the OS change I wanted to check to see if these packages would have problems installing on 10.04 (mostly to double check).  

First I checked my Manage 3rd Party Software to remove them - but all my entries here are blank.  (I should have quite a few actually - I've done a lot of installing and downloading in the last few days).  

I double clicked to re-run them but that failed saying there was a problem with the packages.  So I swapped to Terminal and found the following:   

When I try to install a software package:
  [FONT=Courier New]sudo package install "SMART Product Drivers 10.package"
 Reply:    package: can't open config file /home/test/.mailagent
[/FONT]
If I type in just
  [FONT=Courier New]package
  Reply:   package: can't open config file /home/test/.mailagent
[/FONT]
Same response.  So I uninstalled the mailagent:
  [FONT=Courier New]sudo apt-get remove mailagent
[/FONT]
Which went as expected and re-ran my installer
[FONT=Courier New]  sudo package install "SMART Product Drivers 10.package"
  Reply:   sudo: package: command not found[/FONT]

Learnt something new.  So package seems to rely on mailagent to some extent.  So I re-installed the mailagent
  [FONT=Courier New]sudo apt-get install mailagent

Reply:    Setting up mailagent (1:3.1-65-2) ...
  
          Hmmm.. You don't seem to have an /etc/news/organization file.
          Usually that contains the name of your organization as 
          you want it to appear on the Organization line of outgoing
          articles/patches.[/FONT]

I saw this message when I was on 9.10 at some point so I wasn't worried.  I tried to install again anyway:
[FONT=Courier New]  sudo package install "SMART Product Drivers 10.package"
  Reply:  package: can't open config file /home/test/.mailagent
[/FONT]
So I went ahead and created a dummy /etc/news/organization file with the entry 'None'
[FONT=Courier New]  sudo gedit /etc/news/organization
  "None" - file - save - exit
[/FONT]
So I gave the mailagent another go:
[FONT=Courier New]  sudo apt-get remove mailagent
  sudo apt-get install mailagent
[/FONT]
The re-install didnt mention the /etc/news/organization file.  But when I try to install:
[FONT=Courier New]  sudo package install "SMART Product Drivers 10.package"
  Reply:  package: can't open config file /home/test/.mailagent
[/FONT]
Same error.

-----------------

What's interesting, is checking my Fedora and Debian builds (I've done a lot of learning for only a few days!  But I know a ton about grub 1 and 2 now) - I can't see a /home/test/.mailagent file or folder to copy either.  

The only thing I can think of is I have never setup an email account on my system (I've only been using it for a few days) and maybe the blank Manage 3rd Party Software tab is indicating a different problem.  But I'm out of ideas.  

I also added this as an open question under 112892 as well just in case.  Thanks in advance for your patience and any suggestions you guys have just shout!

I might see if I can remove/reinstall that Manage 3rd Party Software thing.

- Lloyd

---

### Post by KermEd on 2010-05-30
Well, one new discovery.

MailAgent includes a command called Package.  Which seems to have replaced my autopackage command called Package.
[SIZE=1]
[/SIZE][FONT=Courier New][SIZE=1]man package

PACKAGE(1)                                                          PACKAGE(1)

NAME
       package - register package user via mailagent

SYNOPSIS
       package address system version patchlevel [ mailpatches | notifypatches
       ]

DESCRIPTION
       This command is not intended to be run directly  by  a  user,  but  may
       appear  in  any mail whose subject is set to Command. Such mail will be
       processed by the mailagent(1), which will extract all  lines  beginning
       with  @SH,  which  may  specify  this command. The mailagent first sets
       environment variables that will be used by the command.[/SIZE]

[/FONT]Which helps.  so I removed the package again:
[FONT=Courier New]
Apt-get remove mailagent
[/FONT]
Now, how do I re-install autopackage I wonder.  Back to google!

---

### Post by garvinrick4 on 2010-05-31
```
rick@rick-laptop:~$ aptitude show mailagent
Package: mailagent
New: yes
State: not installed
Version: 1:3.1-65-2
Priority: optional
Section: universe/mail
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,737k
Depends: libc6 (>= 2.4), perl, debconf (>= 1.2.0) | debconf-2.0, exim4 | postfix
         | sendmail | mail-transport-agent
Description: An automatic mail-processing tool and filter.
 Mailagent is a mail delivery agent, and can be programmed to respond to mail in
 ways more sophisticated than a mail filtering program like procmail. It is easy
 to configure, and very easy to extend using Perl. Not only can the base
 functionality be extended, new commands and processing methods can be added in
 a modular fashion. 
 
 Obeying lex-like rulesets, mailagent can file mails to specific folders (plain
 Unix-style folders and also MMDF and MH ones), forward messages to third
 parties, pipe them to commands or post them to newsgroups. The filtering
 commands that are executed on the messages can be extended, and may rewrite the
 message headers or body as desired. It can also create and process commands
 based on key words contained in the body of the mail message. 
 
 Mailagent can be used as a vacation program, and can answer mail automatically
 and with more flexibility than the command of that name. A template can be
 provided for the body of the response, and the frequency of vacation mails can
 also be specified. Simple macro substitutions allow parts of the mail header to
 be recycled into the vacation messages, for a more personalized reply. 
 
 Mailagent can also be used to set up a generic mail server, without the hassle
 of the lower-level concerns like error recovery, logging or command parsing. 
 
 Please note that on Debian systems, mailagent requires a catch-all rule saving
 all mail into the user's home directory. Unlike other Mail Delivery Agents such
 as procmail, mailagent is too extensible to be safely made setgid mail, and so
 cannot lock /var/spool/mail mailboxes.

rick@rick-laptop:~$ 

```

---

### Post by KermEd on 2010-05-31
Figured it out.  This should fix the problem for anyone having this problem.  Not bad for only a few days into Linux :P

**Problem**:

Multiple symptoms.

- Manage 3rd party software no longer lists third-party products as installed.
- Running .package files directly results in error messages that  .package files are corrupted.  
- Running the PACKAGE command in terminal generates the following error:

[FONT=Courier New]    package: can't open config file /home/test/.mailagent
[/FONT]
Where test is your username.

**Cause:**

When upgrading your operating system or through regular usage you may accidentally install *MailAgent*.  This *MailAgent* contains a *Package* command that conflicts with the previous *Package* command.

First we need to remove the *MailAgent* which installed a new package file causing the problem.  Then we need to initiate a re-download of *Autopackage*.  *Autopackage* cannot be launched from the repository.

**Solution:**

**Step 1-** Launch *Terminal*
    Enter: [FONT=Courier New]sudo apt-get remove MailAgent[/FONT]

*MailAgent* uninstalls and removes the faulty package command with it.

**Step 2-** Download the following package to your* ~/Downloads/autopackage* folder
    [http://autopackage.googlecode.com/files/autopackage-1.4.2-x86.tar.bz2](http://autopackage.googlecode.com/files/autopackage-1.4.2-x86.tar.bz2)
    *Note: This will install the PACKAGE command again for terminal

**Step 3-** Extract it to *~/Downloads/autopackage*
    *Note: You can place this somewhere else if needed

**Step 4-** Switch to Terminal
    Enter:  [FONT=Courier New]cd ~/Downloads/autopackage[/FONT]
    *Note: You should be in the same folder as the Install script

**Step 5-** Enter:  [FONT=Courier New]sudo ./install[/FONT]
    Enter Password

It will attempt to install the GUI which will likely fail on the URL's for the GUI.  We will install the GUI separately.

**Step 6-** Enter:  [FONT=Courier New]man package[/FONT]

You should see and verify the regular package command succeeded before moving on.

**Step 7-** Download the following package to your *~/Downloads/autopackage *folder
    [http://autopackage.googlecode.com/files/autopackage-gtk-1.4.2.package](http://autopackage.googlecode.com/files/autopackage-gtk-1.4.2.package)
    *Note: This installs your *Autopackage* GUI

**Step 8-** Switch to Terminal
    Enter:  [FONT=Courier New]sudo package install autopackage-gtk-1.4.2.package[/FONT]

You should now have your full auto-package re-installed.  Including support for 3rd Party Applications and Removal of programs again.

:guitar:

---

### Post by KermEd on 2010-05-31
[http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=239](http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=239)

[Jan-Nik]("http://watteimdocht.de/autopackage/forum/memberlist.php?mode=viewprofile&u=2") tipped me off to another detail as well.  

[INDENT]Package <action> <file>
[/INDENT]
Can now also be done with:

[INDENT]Autopackage <action> <file>
[/INDENT]
ie:  autopackage install this_package.package

However, you will likely need to use the work-around above to repair the Manage 3rd Party Software tab.

---

