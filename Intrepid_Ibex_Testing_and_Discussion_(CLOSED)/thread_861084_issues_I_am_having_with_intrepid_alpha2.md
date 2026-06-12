---
title: "issues I am having with intrepid alpha2"
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-07-16
fresh install of a2 with amd64 alternate 
1 selecting shutdown does not shutdown it returns me to the gdm login screen . to shutdown or reboot I must
"sudo /etc/init.d/gdm stop" then "alt+F1" login to the term and "sudo halt (or reboot)"
2 quick search in synaptic does not work regular search does .
3 desktop effects must be reenabled after each boot , I'm using the nvidia-glx-177 driver from the repos.
4 when I open an app that takes text input , for example gedit or a terminal window I have to click on the window to get it to accept text
5 terminal tab to complete sometimes works sometimes doesn't
6 some apps running at shutdown do not restart at login some do
7 audio wierdness as reported by other threads.

with the exception of # 7 I did not have these issues with intrepid upgraded from a fresh install of hardy.

---

### Post by philinux on 2008-07-16
I can comment on two.

1. Yes this happened after an update I got. It replaced the shutdown icon with a logout/change user icon. Adding the shutdown button though still only logs off.

3. Desktop effects for me remain ok after a reboot. Same driver too. Odd.

Keep Testing.

---

### Post by ronacc on 2008-07-16
thanks for the reply , I have been testing since the intrepid repos opened . 
#1 occurs if I select shutdown from the system menu
#3 the compiz-fusion icon is one of the apps that does not restart at login  
I'm going to hold off filing bugs on theese for a few updates to see if any clear up.

---

### Post by BwackNinja on 2008-07-16
for #1, see [https://wiki.ubuntu.com/DesktopTeam/Specs/ExitStrategy](https://wiki.ubuntu.com/DesktopTeam/Specs/ExitStrategy)

---

### Post by Nullack on 2008-07-16
Which ones have you bugged Ronacc?

---

### Post by plun on 2008-07-16
It was so many...:)  FWIW

4. Ok for me, both with start from terminal and GUI, text input OK

5. Dont understand...  ??

6. Not using app memory


Compiz... I have my activation turned off but I must enable
Compiz twice with fusion-icon first start > Reload Window Manager > OK
So apparently something is wrong.

EDIT

No1, broken also for me...  Shutdown > Restart twice and GDM login screen.

---

### Post by MALEADt on 2008-07-16
Upgrading from a hardy install, I'm suffering from #1, #2 and #3 (seems solved on last boot though). Not using session history, so I can't comment #6

---

### Post by Xgen on 2008-07-16
With a fresh install of Alpha II, I'm experiencing 1 -4 with an NVidia driver...but that is the nature of testing development-ware. To temporarily resolve the compiz restart problem, I've added the command 'compiz fusion' to Sessions. Don't know if it is related to #4, but I have to double click twice to gedit any text file in nautilus, and of course, no usplash screen, which has being reported elsewhere..stuff that is not serious enough to Google for a temporary fix.

---

### Post by ronacc on 2008-07-16
@ BwackNinja  what part are you refering to ? that looks like a plan not something they are actualy implementing yet or did I miss something ?

@ Nullack none as of yet  , I will bug all that aren,t already this evening and add my comments to those that are already enterend , I'll report bug#'s back here . note #4 has cleared up

@ plun  4 has cleared up after some update or the other so is ok now . 5 means when you are typing a cmd you can use the tab key to complete a file name like this 
( sudo sh Nvidia<tab> ) instead of having to type the entire file name , it saves time and typing errors  with these absurdly long filenames .  6 when I shutdown I close most apps manulay but there are a few I want to persist like screenlets , awn and fusion icon . right now screenlets does persist (its in autostart) awn doesnt probably because I lose compiz on shutdown fusion icon doesn't but should even if compiz doesnt autostart .

@ MALEADt #3 is still not working for me .

Thanks guys I wanted to see if others were having the same problems or if I had done something stupid during install .

---

### Post by BwackNinja on 2008-07-16
As far as I know, it is a blueprint that was deferred to 8.10 [https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy](https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy) but it may be starting to be implemented now (or something similar is). If I recall correctly, I read somewhere about completely getting rid of all uses of gksu to be replaced by policykit (with some help by packagekit) and also the removal of the 6-option quit dialog (which has been argued as being too complex). How I see it, this would be a symptom of it being implemented. Also - shutdown from the GDM works for me, if that is what you were referring to.

---

### Post by mc4100 on 2008-07-16
> **ronacc said:**
> 
2 quick search in synaptic does not work regular search does .

I think you need the apt-xapian-index package, but it frequently re-indexes so you need to wait, sometimes, before you can use it.

---

### Post by philinux on 2008-07-16
Sorry you're right

Compiz bugs out on reboot.

---

### Post by ronacc on 2008-07-16
@ BwackNinja  yes I was refering to shutdown from GDM ( or anything else for that mater) . selecting system>administration>quit then shutdown produces a relogin , typing shutdown now in a terminal produces a relogin  ,  the only way I can shutdown or reboot is to kill gdm (sudo /etc/init.d/gdm stop ) then login to a term and sudo halt (or reboot) anything else and I'm right back at the desktop . I'm going to file a bug on this one if nobody else has already and I quess we'll find out if it is that blueprint being implemented .

---

### Post by ronacc on 2008-07-16
> **mc4100 said:**
> I think you need the apt-xapian-index package, but it frequently re-indexes so you need to wait, sometimes, before you can use it.

thanks that fixed that one , I wonder why it wasn't installed by default , I never had to manualy install it before .

---

### Post by Nullack on 2008-07-16
Both shutdown and restart are not working - drops to GDM

---

### Post by BwackNinja on 2008-07-16
Same for me too, but ronacc seems to be having problems with it not even shutting down from the GDM. The buttons on the panel and the system menu don't seem to do anything interesting, but shutting down from the GDM works fine for me.

---

### Post by ronacc on 2008-07-16
as promised here is a report back .

# 1  already reported as bug# 248677 , added confirmation
# 3 entered bug # 249260
# 5 entered bug# 249263
# 6 entered bug# 249265

# 4 has cleared itself 
# 2 fix was pointed out by mc4100  above
# 7 is much discussed elsewhere in ths forum

---

### Post by Nullack on 2008-07-17
Good stuff ronacc, hope these get put through the lifecycle quickly unlike some of mine which are yet to be even confirmed

---

### Post by Gina on 2008-07-17
Did a brand new Intrepid install, with a new separate **/home** partition, on a new 500GB SATA drive yesterday.  Used Alpha 2 Alternate CD followed by updates and manual install of nvidia driver.  So everything "on virgin ground".  No imported settings etc.

1. Exit function goes to Logout dialog rather than Shutdown, Restart, Hibernate etc. so shutting down or restarting is a two stage process - logout then Options and choose Restart/Shutdown there.  Sometimes it doesn't restart/shutdown and needs physical restart/shutdown.

2. Wireless on Ralink rt2500 reverts to 1Mhz bit rate on start/reboot.  Needs **sudo iwconfig wlan0 Rate 54M** each restart to get full speed.

Otherwise seems fine though I've yet to do more tests.

---

### Post by ronacc on 2008-07-17
@ Gina   I have been able to get reliable shutdowns by opening a terminal and using  " sudo shutdown -h now "

---

### Post by philinux on 2008-07-17
Just checked compiz. It's supposed be be on but it wasn't.

Installed fusion-icon. (Why is it not called compiz-fusion-icon)

Anyway switched back to metacity the compiz and it's on. Only it looses 4 work spaces and ends up with two. Looks kind of weird when you rotate.

Cant change from 2. Switch back to metacity and 4 workspaces appear.

---

### Post by klange on 2008-07-17
> **philinux said:**
> Just checked compiz. It's supposed be be on but it wasn't.

Installed fusion-icon. (Why is it not called compiz-fusion-icon)

Anyway switched back to metacity the compiz and it's on. Only it looses 4 work spaces and ends up with two. Looks kind of weird when you rotate.

Cant change from 2. Switch back to metacity and 4 workspaces appear.
It's called fusion-icon because that's what it's called. :|

We haven't used the GNOME settings for a while, use CCSM (compizconfig-settings-manager if you don't already have it) to change your viewport settings (we also don't use workspaces, and yes there is a difference, though I'm not even sure what it is) and set the horizontal desktop size to something like 4.

---

### Post by philinux on 2008-07-17
> **WindowsSucks said:**
> It's called fusion-icon because that's what it's called. :|

We haven't used the GNOME settings for a while, use CCSM (compizconfig-settings-manager if you don't already have it) to change your viewport settings (we also don't use workspaces, and yes there is a difference, though I'm not even sure what it is) and set the horizontal desktop size to something like 4.

Whats in a name eh! :lolflag:

I used ccsm. I'll dabble some more.

---

### Post by ronacc on 2008-07-17
ccsm>general options>desktop size    set horizontal virtual size to 4

---

### Post by Gina on 2008-07-17
> **ronacc said:**
> @ Gina   I have been able to get reliable shutdowns by opening a terminal and using  " sudo shutdown -h now "Thanks :)  I do sometimes shut down (or reboot) from command line but generally use the GUI.  I can always set up a launcher to run that shut down method.

---

### Post by philinux on 2008-07-17
Logout then login loses compiz although fusion-icon says it's active.

Have to toggle metacity then compiz to get it back.

Early days but looking good.

---

### Post by ronacc on 2008-07-17
I only shutdown from the cmdline in times of desperation but these are desperate times :lolflag:

---

### Post by philinux on 2008-07-17
> **WindowsSucks said:**
> It's called fusion-icon because that's what it's called. :|



Hover your mouse over the icon in the panel and guess what comes up.
:lolflag:

---

