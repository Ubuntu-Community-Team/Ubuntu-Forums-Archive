---
title: "Upgrading from 7.10 to 8.04 beta AND..."
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by TheGuyWhoGotOn on 2008-04-01
I was upgrading from 7.10 to 8.04 beta HOWEVER even though my sister was warned to stay away from the computer. She switched accounts and played games on Firefox. Now I tried to switch back....the computer locked up. I restarted the computer...Couldn't log in...just the gradient screen...Ok I tried in GIMP failsafe mode...Menus crash. Ok Terminal mode opening Synaptic...No broken packages found...

How can I fix my computer? Hmm it gets better now my computer isn't displaying GUI when it turns on it looks like a terminal...how do I switch it back? Like it's doing this for the login screen...

---

### Post by Herman on 2008-04-01
Boot your Ubuntu Live CD or any Live CD and run a file system check.
You will need to know the linux name for your Ubuntu partion, such as 'dev/hda2', or '/dev/sda3' or whatever. Find that out by looking with Gnome Partition Editor.

When you know which partition Ubuntu occupies, run a command like this, ```
sudo e2fsck -C0 -p -f -v /dev/hda2
``` Where" 'dev/hda2' is your Ubuntu partition, change the command if it's a different partition number.

That should fix it, and if it can't, at least it will give you an error message telling you what to do next.

Regards, Herman :)

---

### Post by TheGuyWhoGotOn on 2008-04-02
> **Herman said:**
> Boot your Ubuntu Live CD or any Live CD and run a file system check.
You will need to know the linux name for your Ubuntu partion, such as 'dev/hda2', or '/dev/sda3' or whatever. Find that out by looking with Gnome Partition Editor.

When you know which partition Ubuntu occupies, run a command like this, ```
sudo e2fsck -C0 -p -f -v /dev/hda2
``` Where" 'dev/hda2' is your Ubuntu partition, change the command if it's a different partition number.

That should fix it, and if it can't, at least it will give you an error message telling you what to do next.

Regards, Herman :)

Thanks...My computer is still booting without GUI, this started when I hit CTRL-ALT-F1...Help please?

---

### Post by Herman on 2008-04-02
What happened when you ran the file system check?
Did the file system check just run and complete satisfactorily, with no error messages? 
Or was there an error message advising you to do something more?

If the file system check has completed satisactorily, then try running 'sudo apt-get update', and 'sudo apt-get upgrade' again to try to complete your update which was previously interrupted.
```
sudo apt-get update
``````
sudo apt-get upgrade
```You can run those from the command line.
Try typing 'startx', to see if your xserver will start,
```
startx
```If you still have trouble, then try
```
apt-get upgrade -f dist-upgrade
```If you get a message at any point that advises you to run 'sudo dpkg -reconfigure -a' then do so.

Here is a nice link that ubuntu demon posted one time about how to deal with problems with the package system (updates and so forth), [What to do when apt-get fails]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")

Regards, Herman :)

---

### Post by TheGuyWhoGotOn on 2008-04-02
Thanks, I get a connection error...Also if I try to reconfigure I need a "superuser" privilege...How can I just reformat my computer? Oh wait I think I know how...Thanks anyways though, I think it would just be easier if I reformatted :P.

---

### Post by varnil on 2008-04-02
LOL YOU HIT ctrl alt F7 and no one is LAUGHING at u for seeing a terminal and not a gui!!??? HIT all the ctrl alt FX on ur keyboard since one of the sessions should be normal ubuntu (i believe its F7). If this fails i recomend getting the alternate gutsy cd and using the repair installation option, then re-upgrading to hardy.

PS: on second thought its kindof natural that no one noticed the ctrl alt f thing since  a majority of linux users switched to it after it got a gui and are unfamiliar with the original aspecs (i still suggest reading up on terminal as it will greatly simplify restoring a semi bricked computer, (most people can't even open a txt doc in terminal... its a shame...)

---

### Post by Herman on 2008-04-02
```
Thanks, I get a connection error...
```Oh, that makes things a bit more of a challenge. :)
```
Also if I try to reconfigure I need a "superuser" privilege...
``` That's easy, just insert the word 'sudo' before the command.
```
How can I just reformat my computer? Oh wait I think I know how...Thanks anyways though, I think it would just be easier if I reformatted :P.
```Sometimes it is easier to re-install, it depends on how much data you have to back up and how much time and effort you put into getting things customized and personalized to your own requirements. Some people can re-install and have everything back to normal within around 45 minutes or less, whereas it can be unpredictable how long it might take to analyse a problem and solve it.
Other people think solving problems is fun and educational though, if time permits.
Do whatever you think will be best for you. :)

---

### Post by TheGuyWhoGotOn on 2008-04-06
Hehe thanks, I just really had music because I've only had Linux for a couple of days. :)

> **varnil said:**
> LOL YOU HIT ctrl alt F7 and no one is LAUGHING at u for seeing a terminal and not a gui!!??? HIT all the ctrl alt FX on ur keyboard since one of the sessions should be normal ubuntu (i believe its F7). If this fails i recomend getting the alternate gutsy cd and using the repair installation option, then re-upgrading to hardy.

PS: on second thought its kindof natural that no one noticed the ctrl alt f thing since  a majority of linux users switched to it after it got a gui and are unfamiliar with the original aspecs (i still suggest reading up on terminal as it will greatly simplify restoring a semi bricked computer, (most people can't even open a txt doc in terminal... its a shame...)

Uh hu...Well I tried all the F's and it didn't work at that time...

---

