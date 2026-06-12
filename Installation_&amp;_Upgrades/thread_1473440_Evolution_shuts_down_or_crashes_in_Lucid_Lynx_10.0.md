---
title: "Evolution shuts down or crashes in Lucid Lynx 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2010-05-05
I have searched the forums and the web to see if anyone else is experiencing this problem but cannot see anything so have started this post.

I upgraded from Karmic to Lucid and after sorting out issues on specialised software (including my printer!) all seems to be working well.  However, in the middle of working with evolution it simply shuts down (or crashes) with no error message or warning.  This happens when I am at the machine or even when I have left it on and am not working on it.  I can see no reason for it and it is not something that happens when I do any particular action in the software.  It simply dies.

Is anyone else experiencing this and is there a reason or solution out there?

---

### Post by iaind on 2010-05-05
I have exactly the same problem, since upgrading from 9.10

Additionally I also find that USB sticks rarely mount, and shutdown sometimes fails, so maybe these problems are all linked, or maybe it is just a buggy release.

---

### Post by luccapenguin on 2010-05-05
Same problem. Absolutely instable.

---

### Post by ASpes on 2010-05-05
Same here too, Evo suddenly kicks out without any warning, cannot point the finger on a specific activity, it just happens.
Never had this problem before, but happened quite a few times in the few days since my stepping to 10.4. 
FWIW my Lucid installation was a clean one from scratch, and, Nvidia apart, was a really smooth one. The only thing I brought along from the old install was the Evo backup for obvious reasons.

Thanks in advance if anybody has any hints about this.

----
ASpes

---

### Post by LANSA301 on 2010-05-05
I'm having similar issue. I'm at my office at this time but someone post a possible solution on my threat.
You can read his response [here ]("http://ubuntuforums.org/showthread.php?t=1472973&highlight=evolution")and try it.
I'll try it tonight when I arrive to my home.
Kindest regards,

---

### Post by ASpes on 2010-05-07
as a small update on my side ... tried recreating the .evolution folder, as suggested in the linked thread, but only the "crash pace" seemed to be slower, as it was getting really annoying.
So I tried and reinstalled Lucid clean from scratch, Evo seemed stable for a while but it just did it again, so I guess all this was to no avail.
The only thing in common was the restoring of Evo from the same backup, something I cannot avoid, so I wonder where is the problem, either in Evolution or LL. The only sure thing is that I had none of this before installing LL.

If any Linux guru out there can hint/find a solution, I'll be deeply grateful.

--
ASpes

---

### Post by SDonatas on 2010-05-07
> **LANSA301 said:**
> I'm having similar issue. I'm at my office at this time but someone post a possible solution on my threat.
You can read his response [here ]("http://ubuntuforums.org/showthread.php?t=1472973&highlight=evolution")and try it.
I'll try it tonight when I arrive to my home.
Kindest regards,


Hi Ive got the same issue here. i'm using x64 bit version. The only way to sort this out is to report a bug in lauchpad (if its not done yet). Evolution is important app in ubuntu (especially for SME users) so I think solutions will appear quickly.

---

### Post by hmgp on 2010-05-07
Upgrading from 9.04 to 9.10 I had problems with evolution.

Upgrading from 9.10 to 10.04 I had problems with evolution.

How can I convince my boss to adopt it in my company?

I too cannot even start evolution after this morning updates...

And yes, I tried to remove the .evotution folder...

This thing is essencial if we have corporate intentions...

Hope there is a solution soon...

---

### Post by claudiaj on 2010-05-08
I am having the same problem with crashing but not in Evolution..yet? It's happens in Firefox. I get completed booted out of the desktop and have to enter my password to get back in. I had a problem with Lucid constantly asking for my password. 

I want to remove Lucid now and wait until it's fixed...anyone know how to?

claudiaj

---

### Post by claudiaj on 2010-05-08
I read the [release notes for installing 10.04]("http://www.ubuntu.com/getubuntu/releasenotes/1004") and found what the problem was, and why I was crashing...RealPlayer was not installed. My crashing issue seems to be resolved.  I was told a long time ago that when all else fails...READ THE INSTRUCTIONS....but I forget...my bad!!

claudiaj

---

### Post by hmgp on 2010-05-10
LOL! 

This is amazing!

I got back evolution.

What I did? Nothing! I just forgot to kill the process, and it only took about 40 MINUTES to come around...

---

### Post by f0rkz on 2010-05-11
evolution is crashing for me as well.  If I leave it idle for some time it simply closes.

Anyone have a fix?

Edit: I backed up ~/.evolution and reinstalled evolution.  Lets hope this works.

---

### Post by gsoundsgood on 2010-05-11
same problem here. it just crashes, apparently randomly, sometimes when I hit the reply or forward buttons, sometimes by itself... looking forward to hear some working solution...

thanks

---

### Post by TCWriter on 2010-05-11
I just switched to Evolution when I moved to 10.04, and it keeps freezing on me - I get a "Formatting message" notice at the bottom of the screen. 

I can move the mouse, but can't view any other emails. 

In a way, I'm glad to hear others are experiencing issues - I'd like to stick with Evo, but with it crashing a couple times a day, I was going back to Thunderbird.

Hopefully, we'll see a fix soon.

---

### Post by happyisland on 2010-05-14
I also have this problem, but strangely it's only occurring on my work computer where I need evolution the most. On my home laptop I still haven't gotten a crash.

I hope someone knowledgeable posts a fix soon, because it is really bad for Ubuntu to have such a core part of the OS be completely unstable. Evolution has already crashed 4 or 5 times in the last 2 or 3 hours.

---

### Post by pmknutsen on 2010-05-17
Same problem here. After upgrading to Lucid from Karmic Evolution frequently goes down silently without warning. No particular event that I have found seems to cause this behavior. Evolution simply seems to close by itself. I've noticed it usually closes on itself when the Evolution window is not active (i.e. I'm working in a different app). Its really weird. Evolution is the most important app I run for business. Does anyone have suggestions where to start looking for clues?

---

### Post by shinglebrook on 2010-05-17
Evolution crashes for me, also seemingly at random. It only seems to do it when connected to my Exchange 2003 server. On re-start of Evolution I always get an error connecting to the Exchange mailbox. I need to close and re-open Evolution again for this to clear itself.

Then Evolution shuts down by itself again .............

---

### Post by happyisland on 2010-05-18
I'm really surprised that there's no fix for this major problem with a core component of Ubuntu.

---

### Post by gabak on 2010-05-18
have u tried to install from scratch karmic then restore all ur emails?
it seem that the bug comes in the new lucid evolution.
if it works for you please let us know,

> **ASpes said:**
> as a small update on my side ... tried recreating the .evolution folder, as suggested in the linked thread, but only the "crash pace" seemed to be slower, as it was getting really annoying.
So I tried and reinstalled Lucid clean from scratch, Evo seemed stable for a while but it just did it again, so I guess all this was to no avail.
The only thing in common was the restoring of Evo from the same backup, something I cannot avoid, so I wonder where is the problem, either in Evolution or LL. The only sure thing is that I had none of this before installing LL.

If any Linux guru out there can hint/find a solution, I'll be deeply grateful.

--
ASpes

---

### Post by johngilbro on 2010-05-19
I've also have evolution quietly closing on its own.  This is a new, simple, lucid install.  I did use the evolution save & restore.  Could that be the culprit?

---

### Post by gabak on 2010-05-19
please do this

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

report the bug the way they say cuz til now i did nt see that report in the bug list.
The sooner ppl report this bug the sooner it will be fixed

---

### Post by ASpes on 2010-05-19
> **gabak said:**
> have u tried to install from scratch karmic then restore all ur emails?
it seem that the bug comes in the new lucid evolution.
if it works for you please let us know,

Sorry Gabak, but I do not want to go back to Karmic, I like better Lucid backgrounds ... :)
Jokes apart, my Evolution backup does come straight from a Karmic install, and, as I said, "The only sure thing is that I had none of this before installing LL."
This looks to me like a memory leak, but I cannot say at what level, what do I know? In my daytime I'm just a humble Win programmer ... if anything on the bright side is that a programme crashing that way would have likely trashed Windows too. Still it's puzzling that an "old" programme like Evo has such issues, usually they have been ironed out since a long time.

Btw, one thing that I seem to notice is that it often pops out when it's starting to check the mail or when shifting the focus from one pane to another. Often, not always. Can anybody confirm that?

---

### Post by f0rkz on 2010-05-19
> **f0rkz said:**
> evolution is crashing for me as well.  If I leave it idle for some time it simply closes.

Anyone have a fix?

Edit: I backed up ~/.evolution and reinstalled evolution.  Lets hope this works.

That didn't work btw.  It is still crashing with no errors reported to X.

I am running it with terminal now, maybe it will report a segfault back to the console...hopefully :(


=====DO NOT DO THE UPGRADE POSTED BELOW=====

---

### Post by gabak on 2010-05-19
For some reason unbeknown to me, the developers of Ubuntu 10.04 updated Gnome desktop environment to version to 2.30 but left the Evolution version as 2.28.  I think that this version of Evolution is really buggy and the decision was a very bad idea.  In this article I will show you how to upgrade your Evolution version to 2.30 and install the Evolution-mapi client so that you can connect to a Microsoft Exchange 2007 server.

To do this we will be using unofficial Ubuntu packages created and maintained by Jacob Zimmerman.  The packages are located on his PPA page.

Step 1:
Install Jacob’s PPA package repository on your system. Open up a terminal session and type the following:

sudo add-apt-repository ppa:jacob/evo230

This will install Jacob’s PPA repository for Evolution 2.30. It will also import the security key.

Step 2:
Update your computer’s repository information.
In the same terminal windows type:

 sudo apt-get update

Step 3:
Next type to upgrade Evolution from 2.28 to 2.30:

 sudo apt-get install evolution

apt will respond by telling you that there are several packages that need installed, upgrade, and removed. Hit the “Y” key to continue.

Now sit back and relax as apt upgrades to Evolution 2.30.

Extra:
If you are in a corporate/school environment that uses Microsoft Exchange 2007 for its email server you can install the evolution-mapi package to allow Evolution to communicate with the server. Remember this is still a very experimental package, however I have found that it is far better in version 2.30 than it ever was is 2.28.
Type this to install evolution-mapi

apt-get install evolution-mapi

This will also need you to hit “Y” to install becuase there are several new packages that get installed to support Evolution-mapi

You should now be able to fire up Evolution and configure it for you email environment.

Note:
The first time that I open Evolution after upgrading I just got a gray screen.  To fix this all I did was reboot.

---

### Post by f0rkz on 2010-05-19
Thanks for the guide.  I'll run this when I get evolution to crash.  I would like to give at least some information for the devs.

---

### Post by gabak on 2010-05-19
i just tried it and it does update evolution to the last version , but it seem to have some issue.
Please try in other pc that u can blow up everything without having any problem.
If somebody know a better way to update it let me know

---

### Post by f0rkz on 2010-05-19
> **gabak said:**
> i just tried it and it does update evolution to the last version , but it seem to have some issue.
Please try in other pc that u can blow up everything without having any problem.
If somebody know a better way to update it let me know

Yeah, it does not work at all.  This completely ****ed my install :((

*Do not upgrade on a live email machine!!!

```
~$ evolution
(evolution:4499): e-data-server-DEBUG: Loading categories from "/home/f0rkz/.evolution/categories.xml"
(evolution:4499): e-data-server-DEBUG: Loaded 31 categories

(evolution:4499): e-utils-WARNING **: /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text
Failed to load module: /usr/lib/evolution/2.30/modules/libevolution-module-mail.so

(evolution:4499): e-utils-WARNING **: /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text
Failed to load module: /usr/lib/evolution/2.30/modules/libevolution-module-calendar.so

(evolution:4499): e-utils-WARNING **: /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text
Failed to load module: /usr/lib/evolution/2.30/modules/libevolution-module-addressbook.so

(evolution:4499): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-evolution-google.so': /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text

(evolution:4499): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-evolution-google.so': /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text

(evolution:4499): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-groupwise-features.so': /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text

(evolution:4499): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-groupwise-features.so': /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text

(evolution:4499): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-evolution-startup-wizard.so': /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text

(evolution:4499): evolution-plugin-lib-WARNING **: Cannot resolve symbol 'startup_wizard' in plugin '/usr/lib/evolution/2.30/plugins/liborg-gnome-evolution-startup-wizard.so' (not exported?)

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_set_active_view: assertion `shell_view != NULL' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_action: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_title: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_update_view_menu: assertion `shell_view != NULL' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_update_search_menu: assertion `shell_view != NULL' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_set_active_view: assertion `shell_view != NULL' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_page_num: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: shell_window_set_notebook_page: assertion `page_num >= 0' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_action: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_view_get_title: assertion `E_IS_SHELL_VIEW (shell_view)' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_update_view_menu: assertion `shell_view != NULL' failed

(evolution:4499): evolution-shell-CRITICAL **: Unknown shell view name: mail

(evolution:4499): evolution-shell-CRITICAL **: e_shell_window_update_search_menu: assertion `shell_view != NULL' failed

```

Furthermore, it is a total PAIN to get the old version reinstalled.

Yeah... uninstalling it completely screwed up GNOME.  I have to reinstall now.

*stuck in enligthenment*

---

### Post by happyisland on 2010-05-19
Whoa. I was considering trying an upgrade to evolution 2.3. Now I'm really glad I didn't after the borkage reported above. Unfortunately now it seems like we're really stuck with this problem.

---

### Post by gabak on 2010-05-19
hey guys i have not this issue for now with my evo maybe cuz i have little amount of emails.
but i have a customer who has that problem.
so i tried to report the bug from my home's computer but cuz i have no that problem i cant from here.
Please if somebody can report it that will be great, here is what ppl from evolution reply to me


[https://bugzilla.gnome.org/show_bug.cgi?id=619109](https://bugzilla.gnome.org/show_bug.cgi?id=619109)
  Evolution | Calendar | 2.28.x

Matthew Barnes <mbarnes> changed:

           What    |Removed                     |Added
----------------------------------------------------------------------------
           Priority|Normal                      |High
             Status|UNCONFIRMED                 |NEEDINFO
                 CC|                            |mbarnes@redhat.com

--- Comment #1 from Matthew Barnes <mbarnes@redhat.com> 2010-05-19 20:42:15 UTC ---
Thanks for taking the time to report this bug.
Without a stack trace from the crash it's very hard to determine what caused
it.
Can you get us a stack trace? Please see [http://live.gnome.org/GettingTraces](http://live.gnome.org/GettingTraces)
for more information on how to do so. Thanks in advance!

-- 
Configure bugmail: [https://bugzilla.gnome.org/userprefs.cgi?tab=email](https://bugzilla.gnome.org/userprefs.cgi?tab=email)
------- You are receiving this mail because: -------
You reported the bug.

---

### Post by gabak on 2010-05-19
question ??
how can i install or upgrade my evo 2.28 to 2.30 ?? just by downloading it from [http://projects.gnome.org/evolution/download.shtml](http://projects.gnome.org/evolution/download.shtml)    ?????

i extract it and i was trying to look for some README or something to tell u how to install it but i see non.
somebody has any idea? i think if it is done manually it should work.

---

### Post by fcornu on 2010-05-20
Hi there,

I just attached a backtrace on ubuntu's bugs tracker

see : [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/578864](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/578864)

Hope it can help :)

---

### Post by happyisland on 2010-05-20
I just submitted one too...

---

### Post by smalle on 2010-05-21
I am running evo 2.30.1.2 (from ppa:jacob/evo230) on 10.04 ... no show-stoppers yet. Finally, idle support! :D

> **f0rkz said:**
> Yeah, it does not work at all.  This completely ****ed my install :((

*Do not upgrade on a live email machine!!!

```
~$ evolution
(evolution:4499): e-data-server-DEBUG: Loading categories from "/home/f0rkz/.evolution/categories.xml"
(evolution:4499): e-data-server-DEBUG: Loaded 31 categories

(evolution:4499): e-utils-WARNING **: /usr/lib/evolution/2.30/libcomposer.so.0: undefined symbol: gtkhtml_editor_insert_text
Failed to load module: /usr/lib/evolution/2.30/modules/libevolution-module-mail.so

...

```

Furthermore, it is a total PAIN to get the old version reinstalled.

Yeah... uninstalling it completely screwed up GNOME.  I have to reinstall now.

*stuck in enligthenment*

I had the same problem, which was just an unlisted dependency.  Upgrade libgtkhtml-editor-common.

e

---

### Post by happyisland on 2010-05-21
That's cool that the 2.3 approach works for you, but I hope a fix gets released for the currently Ubuntu-shipped version. It's what we use for my small business and we really rely on it. As someone who tries to spread the word about Ubuntu I've got to say it's also more than a little embarrassing to have a core, constantly-used component of the OS be completely unstable.

---

### Post by ronjr49423 on 2010-05-23
my evolution is crashing here too. I thought it might have something  to do with mail notifier so I removed that... still no luck. I hope this gets fixed soon.

---

### Post by geoffatmk on 2010-05-24
I too tried to install the latest evolution and got a blank screen that did not recover on rebooting.

I have therefore located a PPA for this install and it worked perfectly for me first time.

If you have courage, go here

[https://launchpad.net/~jacob/+archive/evo230](https://launchpad.net/~jacob/+archive/evo230)

Follow the instructions to add the PPA to your sources and then run an update as indicated.

You may have to go into synaptic to install evolution again but I did not have to do this.  After the udate, evolution just ran from the status bar icon.

I take no responsibility for this advice but it did not give me any problems.  Good luck and post your results if you do it.

As yet, it has not crashed but that does not mean to say it won't!  I will post an update in a couple of days.

Geoff

---

### Post by marcadon on 2010-05-24
I get the same problem too.

Originally upgraded then did a fresh install to try to fix this and other issues.

---

### Post by marcadon on 2010-05-24
Oh how Ironic.

I just tried to open the 'welcome' email from this forum and evolution crashed!

---

### Post by geoffatmk on 2010-05-24
Well it is still crashing but at least now it appears to be for a consistent reason.

Not every time but on occasion when I go to open a new mail normally (or maybe always actually) with an attachment, bang it disappears.  This leads me to think it is a database back end problem.

I read somewhere on one of the forums that people thought it might be the database and this certainly support this view.

Rebooting does not overcome the issue so the attachment (if that is what it is) has corrupted the database and will not let me read the email it is in or open it to view it.

Thanks goodness all my emails in and out are copied to my gmail account or I would be stuffed.

The upgrade is stable apart from that as far as I can see and is not crashing on its own as it was before.

G

---

### Post by randyclark on 2010-05-24
I have also struggled with this problem and seem to have solved it. I did an upgrade to Lucid and have always kept my home partition separate. In this case here is what seems to have done it for me:

(1) Upgraded to Evolution 2.3 as suggested in this thread

(2) Renamed my .evolution directory to allow Evolution to recreate it.

These two things did not solve it however, and I realized that when I started Evolution it still remembered my mail account settings. I did a search for files containing the e-mail accounts and found the following file:

/randy/.gconf/apps/evolution/mail/%gconf.xml

I deleted this file as well after backing it up. Restarted Evolution and got the setup wizard. Entered my e-mail account information in the wizard and have been running without a crash most of today. 

Randy

---

### Post by geoffatmk on 2010-05-26
Randy,

I have 12 email accounts and a pretty complex evolution setup so before I try your suggestion (I should not have to, what is happening with the evolution development team?) I would like to have confirmation that it is not crashing on emails that have attachments, on both POP and IMAP accounts.

Can you gove some more feedback as this is now more than an annoyuing problem, it is affecting my business communication.

Has anyone else tried Randy's suggestion?  Could they also offer feedback?

G

---

### Post by gabak on 2010-05-27
i installed the new evolution 2.30 and i still have problem.
now soon as i select some email with calender information it close it" s self.

the good news i could install it,

Does anybody know maybe if i install an older version it will be more stable?

---

### Post by geoffatmk on 2010-05-27
I am sure you could but as we do not know if it is an evolution or an ubuntu problem you may have to go back to Karmic which (I believe) installs 2.26.  That at least was stable but it seems a pretty retrograde action to have to take.

G

---

### Post by happyisland on 2010-05-27
> **geoffatmk said:**
> Randy,

I have 12 email accounts and a pretty complex evolution setup so before I try your suggestion (I should not have to, **what is happening with the evolution development team?**) I would like to have confirmation that it is not crashing on emails that have attachments, on both POP and IMAP accounts.

Can you gove some more feedback as this is now more than an annoyuing problem, **it is affecting my business communication.**

Has anyone else tried Randy's suggestion?  Could they also offer feedback?

G

I strongly concur with the bolded parts above. This is pretty frustrating, and the bug is still unassigned.

---

### Post by dmafcoi on 2010-05-27
same issue here, apparently random evolution crashes

---

### Post by bixejo on 2010-05-28
Same issue here in two different Lucid 64bit systems. Apart of all it's been discussed in this thread, I've found something: there are some folders that I cannot compact to definitively remove deleted messages. When I try to do it, it says "Error while compacting folder", and when I click in the warning icon (in the lower left part of Evo window) it says: "Error while compacting folder. Summary and folder do not match, even after synchronizing" (or something like that, I'm translating from Spanish).

I closed Evo and manually removed summary and other info related to this folder. (files *.cmeta, *.ibex.index.data, and *.ibex.index) for Evo to rebuild them at next time it reads the folder. It indeed does so, then there is no problem for a while, but after some days the problem appears back again, probably in some other different folder :confused:.

I don't know whether it could be related to Evo'  random shutdowns, but that's the only strange behavior I've observed in Evo (apart from the main and hard problem of this thread, of course).

Regards,

---

### Post by pwebster25 on 2010-05-28
For a couple months, evolution has been corrupted on my machine, in that it won't let me setup a new account.  In the setup wizard, the "forward" button is greyed out.  So you can tell it to do something but it won't proceed.  I have upgraded from Karmic to Lucid in this time frame and that didn't fix it.  I have uninstalled evolution and reinstalled and that didn't fix it.  I have upgraded to the jacob ppa referred to in here. With no avail.  I will try to do what you said as far as clearing everything out and then reinstalling.  I think there is just something left in there.  Any ideas on completely purging evolution and then reinstalling?  I'm afraid that the evolution database is used for other gnome functions.  I don't want to mess that up.

I would like to look into combo of davmail gateway and thunderbird to connect to my exchange 2007 server through OWA.  Is that an option others have tried?

---

### Post by therblack on 2010-05-28
Well, I was able to install 2.30.1 from ppa:jacob/evo230 and I can start it okay and read my mail (using mapi) :-)

But, it crashes when I try to send mail.  I have tried with a clean .evolution and the same thing happend

---

### Post by ASpes on 2010-05-28
> **bixejo said:**
>  ... there are some folders that I cannot compact to definitively remove deleted messages. When I try to do it, it says "Error while compacting folder", and when I click in the warning icon (in the lower left part of Evo window) it says: "Error while compacting folder...

Bixejo,

Not sure if this can help your "compacting folder" issue, but got into that when I was still on Karmic. My solution has been to export everything to a backup file with "backup settings", and then restore it all with the "restore settings" function. This forces all reindexing a-new. I dare to say it worked for me as it never happened again.

As for the crashing issue, it still goes on and happens countless times each day.
I filed a bug-buddy report, but got a message they found "no sign of evolution code in trace".

It still seems to me that the most times it pops off are when it does a mail check, either forced with F9 or automated, which could be explain the crash when "unattended" .

Keeping crossed fingers in fear of the crash, makes typing a message rather difficult ... :)

---

### Post by pwebster25 on 2010-05-29
Mine may be a different, but related problem.  I have uninstalled every part of evolution I could without uninstalling the whole database.  I backed up and changed the names of all the .xml files in the /home/paul/.gconf/apps/evolution folder so that they could recreate themselves (they did). I renamed the .evolution folder in my /home directory so that it would recreate itself (It did). Then I reinstalled evolution and evolution-mapi from synaptic. I restarted. I opened evolution and it says (Null) in the window header.  I assume that means it is missing a critical piece.  I don't know what this is.  It didn't ask me to set up a new account, as I was hoping.  If I go to edit -> Preferences in Evolution it crashes.  Any idea how to force an account setup, maybe through the terminal?  Is there a file I need to create?  I have attached a screenshot.

FYI:
I'm on 10.04 and am using the Jacob ppa, per this thread.

---

### Post by pwebster25 on 2010-05-31
I finally gave up on evolution.  I setup davmail gateway and then setup Thunderbird 3 with a lightning extension.  Syncing with the server is a little bit slow but it works.  The slowness may be my own network, as my modem has been wigging out recently. I more/less followed [this tutorial]("http://karuppuswamy.com/wordpress/2010/05/13/how-to-integrate-thunderbird-with-ms-exchange-to-replace-ms-outlook") as well as the one on the davmail site at sourceforge.

---

### Post by happyisland on 2010-06-02
I was really hoping that the solution wouldn't be abandoning Evolution entirely - I appreciate the integration into Gnome and tend to prefer the default Ubuntu stuff for work PCs since they're theoretically more stable. It's looking more and more like we'll have to switch to Thunderbird though, since Evolution in 10.04 is just TERRIBLE. I can't remember a piece of non-beta software performing so poorly in recent memory...

---

### Post by pwebster25 on 2010-06-02
happyisland-
I agree.  I have tried hard to be loyal to default software but in this case I just couldn't get it to work (not even a little bit).  I am happily integrating Thunderbird.  I love the tabbed interface.  It seems to stay in sync with my MS Outlook account online and the interface is a lot easier to manage than the OWA. OWA is really a pretty slick interface in IE but in firefox it quite inefficient.

---

### Post by egran2ca on 2010-06-03
This bug has been reported on Launchpad, but only 3 people (including me) have said it's a problem. If everyone who's complained in this thread went to the site, clicked on the 'does this affect you' and said 'yes', it might be given higher priority for a fix.
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183)

---

### Post by happyisland on 2010-06-03
I'm one of the other people. Please go vote on launchpad, people! We need to get this bug fixed!

---

### Post by gabak on 2010-06-03
hi i end up using thunderbird , now i m ubuntu 64 bits and everything was better. :D
i have one question , does anyone here is paying to canonical for support?
what if anyone of us call them saying this problem?? what will they do to fix it?

---

### Post by gabak on 2010-06-03
just load evolution with 2 or 3gb of emails and it will crash. I have a customer who has many years of emails and when i import all his emails from thunderbird from windows this problem started to happend.
If you have few emails , evolution works just fine. Even after an update to evolution 2.30

---

### Post by gabak on 2010-06-03
i wonder if it is ubuntu problem or if it happen in other linux distro too?

---

### Post by bhart007 on 2010-06-03
Having the same issue here.. Fresh install of 10.04, and according to a different thread I found I even upgraded to Evo 1.30.  Deleted the .evolution folder to recreate the profile.  Using only the evo mapi plugin.. Evo starts up, prompts me to create a new profile.  Entering Name and address info, choose Exchange MAPI, enter server name and username then Authenticate.. enter password.  After that it thinks for about 4 seconds then crashes with a Segmentation Fault.

---

### Post by HX_unbanned on 2010-06-04
Memo crashing workaround:

evolution (2.30.1.2-3ubuntu1) maverick; urgency=low

  * Remerge from debian unstable, remaining changes:
   + debian/control:
      - add Vcs-Bzr tag
      - don't use po-debconf
      - build-depends on libpst, python and shared-mime-info
      - don't split documentation since it goes to langpacks
      - evolution-plugins-experimental replaces evolution-plugins (<< 2.27)
      - updated descriptions to reflect binary installs
      - build-dep on liblaunchpad-integration-dev
      - remove libgtkimageview-dev build-dep: not in main, seems crashy right
        now
    + debian/docs:
      - renamed evolution-common.docs
    + debian/evolution-2.2.desktop:
      - compatibility .desktop for users upgrading
    + debian/evolution.gconf-defaults:
      - don't display unstable warning on startup (Ubuntu: #91799)
    + debian/evolution.install:
      - install the autostart and compatibility desktop entries
      - install webdav and python but not hula and print-message there
    + debian/evolution-mail.desktop:
      - don't reapply this ubuntu change and use only one menu entry
    + debian/evolution-alarm-notify.desktop,
      debian/evolution-alarm-notify.desktop.in,
      #debian/patches/64_translate_autostart_strings.patch: #
      - autostart desktop file to start evolution-alarm-notify with the session,
        translate the entry
    + debian/evolution-dev.install:
      - detail the .so to install
    + debian/evolution-plugins.install,
      debian/evolution-plugins-experimental.install:
      - install the .so in binaries corresponding to the upstream options
    + debian/patches/01_dont-ship-evo-mail-notifier.png.patch:
      - don't ship that change that debian added without reason
    + debian/evolution.preinst, debian/evolution.templates:
      - don't display debconf template on upgrade
    + debian/patches/03_lpi.patch:
      - launchpad-integration patch
    + debian/patches/62_no_upstream_email_notification_by_default.patch:
      - don't enable the notification icon by default since the message
        indicator
        is running
    + debian/patches/10_desktop_shortcuts.patch
      - Adds desktop shortcuts for the messaging menu.
    + debian/rules:
      - don't use -Bsymbolic-functions to workaround memos crashing
      - don't use debconf translation there
      - use --disable-scrollkeeper --enable-python configure option
      - use --disable-inline-plugin: dep not in main, seems crashy right now
    + debian/patches/90_autoconf.patch:
      - refresh autotool


Segmentation Fault fix:

evolution (2.30.1.2-3) unstable; urgency=low

  * debian/patches
    - 03_fix-segfault-on-some-mails-display added.  (LP: [#584536]("https://launchpad.net/bugs/584536"))
    - 04_fix-crash-when-viewing-closing-mails-quickly added,
      cherry-picked from upstream. Fix crash when opening/closing mails
      quickly.                                                  closes: #582564
  * debian/evolution.links dropped, upstream doesn't ship them in /usr/bin for
    good reason, they're supposed to be called from evolution not directly by
    user, and the interface might not be stable.                closes: #582491
  * debian/watch updated to order the first directory too.
 -- Didier Roche <[didrocks@ubuntu.com]("https://launchpad.net/%7Edidrocks")>   Mon, 31 May 2010 12:43:31 +0200

I think that updating to this build should fix some leftover blockers ...

Put this to PPA ( backport for Lucid ) or compile by yourself ;)

---

### Post by ar-jar on 2010-06-04
Same problem here. Upgrade from 8.04 to 10.04. Took me a while to realize that it wasn't me who was starting to senile but the application closing down by itself after a while. This is definitely a major bug. I don't particularly like the Thunderbird GUI nor all the weird defaults when setting up accounts (at least in the Windows version) so I'd like to stick to Evolution if at all feasible. A thank you in advance to the devs working on this! -A

---

### Post by Linuxforall on 2010-06-04
> **ar-jar said:**
> Same problem here. Upgrade from 8.04 to 10.04. Took me a while to realize that it wasn't me who was starting to senile but the application closing down by itself after a while. This is definitely a major bug. I don't particularly like the Thunderbird GUI nor all the weird defaults when setting up accounts (at least in the Windows version) so I'd like to stick to Evolution if at all feasible. A thank you in advance to the devs working on this! -A

You can add the Evolution 2.30 via [http://www.webupd8.org/2010/06/install-evolution-230-in-ubuntu-1004.html](http://www.webupd8.org/2010/06/install-evolution-230-in-ubuntu-1004.html)

---

### Post by ar-jar on 2010-06-04
Thanks, I'm trying it out right now. As you said, 2.30 doesn't seem entirely finished yet. The message window always ends up in the lower right corner for instance. But I can take that as long as it's stable... -A

---

### Post by ar-jar on 2010-06-05
A bit off-topic but not quite: I don't find any "backup plugin" or any other form of backup command like in the old versions. 2.30 is giving me a lot of error messages, marking folders as not read even though they are etc etc. I was about the clean the mail files and start over and then import the latest backup but it looks like I would have been in trouble... -A

Edit: Ok, i did an update and got the backup plugin and some other stuff too. There is hope.

---

### Post by beow on 2010-06-05
Have installed 2.30.1.2 from evo230 ppa. Removed ".evolution" and deleted all accounts under "Preferences". 

Exchange OWA does not work for me. BUT, hold your thumbs, Exchange MAPI over a VPN seems to work... at least for mail and contacts. Calendar halted at 6% updating. We are using Exchange 2003.

So there is some hope that MAPI is coming along which would be REALLY nice... :)

---

### Post by beow on 2010-06-05
After a restart also Calender works, looks very promising... :)

---

### Post by jwood1961 on 2010-06-05
Yes, I have the same problem, from a clean install of Lucid on a Samsung N140 netbook.Only seems to affect evolution. Sometimes when I'm working on it, sometimes when the machine is basically idle.

I' read the link to the installation notes and couldn't find anything relevant for evolution or for real-player.  Realplayer isn't in the base repositories, so what can it have to do with it?

Kind Regards
JW

---

### Post by ar-jar on 2010-06-05
2.30 seems to have the same problem here so no cigar. -A

---

### Post by happyisland on 2010-06-06
If 2.30 also has the problem then it's looking like we've got bigger problems. Is this a gnome keyring issue, as it is listed on launchpad?

---

### Post by geoffatmk on 2010-06-07
Hi

Earlier I recommended the PPA installation but then found that it was still crashing with emails that contained attachments.  I meant to update this forum earlier but forgot so apologies.

When I looked into it I found that the update did not seem to work properly and I had to manually mark about four or five items in Synaptic to run an update.  One of them was for a part of the evolution database.  Once this was done the crashing stopped and it has worked perfectly since.

This has (for me) been the worst upgrade experience to date.  I am nearly back where I was before it with only my xsane scanner giving me problems.

Hope this helps some of you.

G

---

### Post by Rodneyck on 2010-06-09
I use evolution for work, exchange 2003 server, and now I get this crash starting today whenever I start a new message, reply, forward, etc. 

It appears through a simple Google search that this problem is quite common and goes back several years. I have no idea what I am going to do for an email client now.

---

### Post by happyisland on 2010-06-09
Now I'm starting to see this problem on my home computer as well as my work computer. 

Please, anybody who's experiencing this bug: go post on launchpad! It's still unassigned, which leads me to believe that it's still not being taken seriously. Maybe if we get more people reporting the bug we'll be able to get a fix for it.

Here's the link to the bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/578864](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/578864)

---

### Post by geoffatmk on 2010-06-10
After significant stability the updates today started evolution crashing again.  I think the problem is that Jacob's update files are not in the required folder and I have written to ask him to put them in.

G

---

### Post by Micha401 on 2010-06-14
> **gabak said:**
> 
Step 1:
Install Jacob’s PPA package repository on your system. Open up a terminal session and type the following:

sudo add-apt-repository ppa:jacob/evo230

This will install Jacob’s PPA repository for Evolution 2.30. It will also import the security key.

Step 2:
Update your computer’s repository information.
In the same terminal windows type:

 sudo apt-get update

Step 3:
Next type to upgrade Evolution from 2.28 to 2.30:

 sudo apt-get install evolution

apt will respond by telling you that there are several packages that need installed, upgrade, and removed. Hit the “Y” key to continue.

Note:
The first time that I open Evolution after upgrading I just got a gray screen.  To fix this all I did was reboot.

I just did this on lucid_64 and it worked like a charm. Many thanks for that repository. Evolution started right away.
I stumbled upon 2.30 by chance. I wasn't aware that in lucid isn't a current release of Evolution.
To hold back a central peace of software is a bad choice by Canonical.

---

### Post by Rodneyck on 2010-06-14
> **Micha401 said:**
> I just did this on lucid_64 and it worked like a charm. Many thanks for that repository. Evolution started right away.
I stumbled upon 2.30 by chance. I wasn't aware that in lucid isn't a current release of Evolution.
To hold back a central peace of software is a bad choice by Canonical.

This did not work for me. 2.30 will not connect to Exchange 2003 and Evolution still crashes on repy, forward, etc.

---

### Post by ar-jar on 2010-06-24
I am happy to report that my Evolution ran over-night (has never happened after the upgrade to 10.04 before) with yesterday's update from the "jacob ppa". Looks also like at least one bug report on the crash bug has been fixed (#530760 in launchpad). -A

---

### Post by Hedley on 2010-06-24
> **Micha401 said:**
> I just did this on lucid_64 and it worked like a charm. Many thanks for that repository. Evolution started right away.
I stumbled upon 2.30 by chance. I wasn't aware that in lucid isn't a current release of Evolution.
To hold back a central peace of software is a bad choice by Canonical.



Out of frustrated desperation, I tried this. It's been several hours now, and Evolution hasn't crashed once (compared to a previous average crashing rate of every ten minutes). 

HB

---

### Post by Hedley on 2010-06-24
> **Hedley said:**
> Out of frustrated desperation, I tried this. It's been several hours now, and Evolution hasn't crashed once (compared to a previous average crashing rate of every ten minutes). 

OK, it still hasn't crashed, so that's good. 

The bad news is that 2.30.2 has a few other annoying new bugs. For instance, the calendar seems to forget my view settings. Also, 'read' messages in the inbox randomly get re-marked as 'unread'. I wasn't all that keen on Thunderbird's calendar, as I recall, but if Evo/Ubu doesn't get fixed up a bit, I might soon be revisiting it.

---

### Post by happyisland on 2010-06-25
Great! I'm going to try this, because the first feedback on the launchpad 'bug fix' was that it didn't work.

Here we go...

---

### Post by Pluscom on 2010-06-25
> **geoffatmk said:**
> I have searched the forums and the web to see if anyone else is experiencing this problem but cannot see anything so have started this post.

I upgraded from Karmic to Lucid and after sorting out issues on specialised software (including my printer!) all seems to be working well.  However, in the middle of working with evolution it simply shuts down (or crashes) with no error message or warning.  This happens when I am at the machine or even when I have left it on and am not working on it.  I can see no reason for it and it is not something that happens when I do any particular action in the software.  It simply dies.

Is anyone else experiencing this and is there a reason or solution out there?

Evolution problems have been driving me nuts.  Deleting the .cmeta files and .index files works for a while but the problems keep coming back.  As email is so important to me I have reverted to Hardy Heron (8.04).

After installing Lucid Lynx my computer slowed down, my webcam quit plus other annoying problems.  It reminds me of my upgrade to Vista, the one that drove me to Ubuntu in the first place.

---

### Post by ebasa on 2010-06-25
I finally gave up on Evoultion, installed claws-mail it works like a charm.

---

### Post by happyisland on 2010-06-25
I don't want to jinx it, but following the instructions above for the jacob PPAs has seamlessly provided me with an Evolution that hasn't crashed in over 1.5 hours of use! To put this in perspective, the Ubuntu-provided Evolution was crashing on an average of every 10 minutes! 

Look like we've got a winner!

---

### Post by bobzr on 2010-06-26
I don't think installing from PPA is what users are expected to do for a main program like Evolution, especially in a LTS release. 
This bug is really a disaster, I liked Evolution so much but I'm now considering switching to Thunderbird. Lightning for TB 3 is still beta but yet seems to work better than Evo, which is supposed to be stable.
If it's left idle for some time it simply closes.
Moreover I'm keeping on deleting all those .cmeta, .ibex.index, etc files in the mail folder to get rid of the "error even after sync" message.

---

### Post by geoffatmk on 2010-06-26
I would urge caution.  When I first started using evolution it was exaxtly as you describe the Thunderbird Lightning beta.  The problem is that as these systems become more complex they become harder to control.  You could end up in the same place in 6 months feeling very frustrated.

The best thing to do is to conitue to notify the developers of the problem as it is a serious (and as you point out) product threatening issue.

---

### Post by kevinanchi on 2010-06-28
**Evolution crashes in Lucid Lynx 10.04 many times **

---

### Post by luccapenguin on 2010-07-02
After last updates, Evolution now seems OK...
No shut down, today. No ONE! It's a miracle!!!!:P
Hope it will last til tomorrow...;)

---

### Post by outleradam on 2010-08-23
wow... this still has not been fixed?  Evolution does not crash on my computer.  It waits until I hit send and then does not send the frakin' message.  It just exits the email writer gracefully and does not send my message.

---

### Post by jdandison on 2010-08-23
I've had this problem on both x86 & x64 editions of 10.04. Seems to have something to do with IMAP HTML emails.

I have Evolution hooked up to Exchange as well (via OWA), and HTML & plain text emails open properly.

Once I move to an IMAP account and click on a message, Evolution just crashes - Segmentation Fault in imap_parse_body(), so it's definitely IMAP-related.

Here's the bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/554367]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/554367")

---

### Post by bixejo on 2010-08-30
> **jdandison said:**
> I've had this problem on both x86 & x64 editions of 10.04. Seems to have something to do with IMAP HTML emails.

_[...]_
I've never had IMAP accounts (only POP) and the problem was still present. I made a fresh install (it was a direct 8.04 -> 10.04 upgrade) and looks like it vanished. The devil is in the details... :confused:

---

