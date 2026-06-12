---
title: "Update manager"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by topic58 on 2007-04-21
I had Update manager 0.45.2 but today there was another update to download - update manager 0.45.3. And after downloading that one I lost the chance of updating to 7.04... The message: Upgrade to 7.04 is not there anymore. What to do? I was about to upgrade to 7.04 and just wanted the update manager go give me the latest updates before that.

---

### Post by sharke on 2007-04-21
which version are you updating from.
Regards
Sharke

---

### Post by topic58 on 2007-04-21
Edgy 6.10

---

### Post by topic58 on 2007-04-21
Maybe this will solve it?
$ gksu "update-manager -c"

---

### Post by VosaxAlo on 2007-04-21
Hi,

yes, I have the same problem.
This morning (here saturday 21 april) I have made an update in Edgy before starting to upgrade to Feisty. One package was the update-manager itself. From 0.45.2 (edgy-updates) to 0.45.3 (edgy-proposed). Now no way to display the upgrade button for Feisty.

any idea?

@topic58: I have tried 20 times and more with gksu "update-manager -c", but no success. I believed that was a server problem (too much requests), but I have tried from 09:00 to 11:30 time without success.

---

### Post by topic58 on 2007-04-21
Or maybe this:
sudo apt-get dist-upgrade

---

### Post by VosaxAlo on 2007-04-21
No.

this command is like a check in the update-manager. The command display that all is up to date.
The problem is still present. No way to upgrade to Feisty for now!!
Maybe this is a bug in the new version of update-manager?

---

### Post by topic58 on 2007-04-21
Try this thread.
[http://ubuntuforums.org/showthread.php?t=286599&page=3](http://ubuntuforums.org/showthread.php?t=286599&page=3)
maybe this can be of any help?

---

### Post by topic58 on 2007-04-21
Or try to add the Feisty reps instead of the Edgy reps. Then maybe the update should work. Just a suggestion. Someone who got a better solution?

---

### Post by topic58 on 2007-04-21
There seems to be a lot of problems upgrading from Edgy to Feisty, so maybe there is a good idea to wait for 7.10 or whatever. Like in Edgy (6.06 to 6.10)=D>

---

### Post by PetruM on 2007-04-21
Hi,

I've got problems when trying to upgrade as well. First I've tried doing it from the CD, no luck (no dialog appeared asking to upgrade and the command given in the tutorial does not work). Then I have decided to use the updates manager - no luck as well, it just hangs at 'Fetching file 111 of 113'. :( 

I hope someone will fix this as soon as possible.

---

### Post by graha on 2007-04-21
i have different problem it gave me this 

warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by VosaxAlo on 2007-04-21
> **graha said:**
> i have different problem it gave me this 

warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

BTW me too. In the terminal I receive the same messages.

---

### Post by vasimakhtar on 2007-04-21
I am on the same line. What is happening here? Trying since three days to upgrade from 6.10 to fiesty but no luck. My internet is fine and it still gives messages like check your internet connection, network connection and update failed.
Any suggestions?
thanks

---

### Post by papernik on 2007-04-21
ok, here same problem, dist upgrade button disappared after updating "update-manager".

Any solution ?

---

### Post by VosaxAlo on 2007-04-21
> **vasimakhtar said:**
> I am on the same line. What is happening here? Trying since three days to upgrade from 6.10 to fiesty but no luck. My internet is fine and it still gives messages like check your internet connection, network connection and update failed.
Any suggestions?
thanks

Today I have read for a while in this forum. A poll say that 50% users have no problem with upgrade, and 50% have a lot of problems. 
So I begin to believe that the disappearance of the upgrade button is intentional from Canonical. 
Too many people with trouble = bad advertising for Ubuntu and family.

Better is to stop users upgrading for now. 
I hit it?

---

### Post by william_nbg on 2007-04-21
Yup!

Same problem here.

Maybe he's right: better to wait.

I was sitting here thinking about updating when I received an update for the update manager. Sine, the magic upgrade button is gone.

---

### Post by DougieFresh4U on 2007-04-21
Well you can always bring up your sources list and change all Edgy to Feisty then **sudo apt-get update** then **sudo ap-get dist-upgrade**

---

### Post by pebo on 2007-04-21
> **DougieFresh4U said:**
> Well you can always bring up your sources list and change all Edgy to Feisty then **sudo apt-get update** then **sudo ap-get dist-upgrade**

Worth reading the wiki for that [here]("https://help.ubuntu.com/community/FeistyUpgradesManual") and note the warning > Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. It is highly recommended that you use the automatic upgrade instructions on FeistyUpgrades instead.

---

### Post by mvo on 2007-04-21
Hi,

If 0.45.3 does not work for you, could you please try to:
$ mv .update-manager .update-manager.old

and see if that gives you the "upgrade" button back? 

If that does not help,can you please run:
$ sudo apt-get install update-manager=0.45.2

and see if that makes the button re-appear? In any case, please report it as a bug against update-manager. Its a bug that seems to be cause by a chance that is intended to help people behind (transparent) proxy servers.

Cheers,
 Michael

---

### Post by VosaxAlo on 2007-04-21
> **mvo said:**
> Hi,

If 0.45.3 does not work for you, could you please try to:
$ mv .update-manager .update-manager.old

and see if that gives you the "upgrade" button back? 

If that does not help,can you please run:
$ sudo apt-get install update-manager=0.45.2

and see if that makes the button re-appear? In any case, please report it as a bug against update-manager. Its a bug that seems to be cause by a chance that is intended to help people behind (transparent) proxy servers.

Cheers,
 Michael


Ok. I have made the downgrade from update-manager 0.45.3 to 0.45.2 and the upgrade button now is present !
I will go to launchpad and verify if this bug is already present or not. If not i will open one.

thank's

---

### Post by lesliem on 2007-04-21
Hi,
Yes had same problem as others tried upgrading from edgy to feisty, seemed to download upgrade, but when installing stopped with this error.
E: /var/cache/apt/archives/spampd_2.30-15_all.deb: subprocess new pre-removal script returned error exit status 4.
Rebooted after failure update manager icon showing 680 updates waiting but will not start.
Checked synaptic repositories changed to fiesty? but no upgrade.
Does spamassassin [as above /spampd ] have anything to do with this??
At least my system still works.

Will keep trying :confused: 

lesliem

---

### Post by Chriss.Hi on 2007-04-21
same prob here - please post a fix as soon as you've found one, please

---

### Post by Chriss.Hi on 2007-04-21
**Solution:**
Remove the directory ~/.update-manager

---

### Post by lduperval on 2007-04-21
I am seeing this also.I tried a couple of things: changed all instances of edgy to feisty in sources.list, I think I tried something else also, but the result is the same: I don't get the Upgrade button. 

I am looking to downgrade to 0.45.2 of update-manager.

Right now, when I run synaptic, it says there are 900+ packages to upgrade. But from what I have read, using this option to update  system is problematic at best.

Is there any information anywhere on downgrading only one package?

L

---

### Post by lduperval on 2007-04-21
Aha! Found it! Search for package manager in synaptic, then go to Package > Force Version (or Ctrl-E). Select version 0.45.2. 

Exit synaptic and go to update-manager and the button will be back.

So I am about to upgrade now.

L

---

### Post by william_nbg on 2007-04-22
> Aha! Found it! Search for package manager in synaptic, then go to Package > Force Version (or Ctrl-E). Select version 0.45.2.

Exit synaptic and go to update-manager and the button will be back.

So I am about to upgrade now.



Let me know how that goes!!!

I need my box for work, and can't afford to be down too long - :)

---

### Post by lduperval on 2007-04-22
It went great! I downloaded, installed and so far, I haven't had any issues. I haven't tested much either. However, mail is working, NNTP is working, Firefox is working, some other (nonstandard) things I had in place are still working. The only big part I haven't tested is printing and scanning. Once I try those, I will report if I have issues.

So for me, it was smooth sailing.

L

---

