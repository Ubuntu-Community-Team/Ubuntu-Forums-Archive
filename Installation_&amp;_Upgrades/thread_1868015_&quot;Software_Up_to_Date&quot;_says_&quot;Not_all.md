---
title: "&quot;Software Up to Date&quot; says &quot;Not all updates can be installed&quot;..."
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by wmcbrine on 2011-10-23
After upgrading to 11.10, I get the above message, with the options of "Partial Upgrade" and "Close". If I select "Partial Upgrade", I'm told "Your system is up to date", and it says it's cancelling the upgrade. But if I select "Close", I get a message that the "Software index is broken", with advice to run Synaptic or apt-get install -f. Yet neither Synaptic nor apt-get thinks there's any problem to fix! How do I solve this?

---

### Post by Old_Grey_Wolf on 2011-10-23
To fix the partial updates try entering these commands in a terminal
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by wmcbrine on 2011-10-24
Thanks... but, that didn't work.

I should add that there's a little arrow-in-sun icon in the menu bar that, when I click on it, says "Error: BrokenCount > 0". This is another place where it tells me to run Synaptic or apt-get... but like I say, *those* programs report 0 broken packages.

The icon disappeared when I removed lists/*, then reappeared after the apt-get update.

---

### Post by scottku on 2011-10-24
I have also run across this issue on all three of the computers that I upgraded from 11.04 to 11.10.  On 2/3 machines, I have managed to fix it somehow.  On the third machine, I can't seem to make the message go away.  Following Old_Gray_Wolf's suggestion did not work for me either.

---

### Post by Old_Grey_Wolf on 2011-10-24
Post the output of this command ```
cat /etc/apt/sources.list
```

Edit: before you do that command, try opening the Ubuntu Software Center and in the dialog box see if it is saying that you needed to repair some broken dependencies. If so, clicked on the Repair button.

---

### Post by Old_Grey_Wolf on 2011-10-24
> **scottku said:**
> I have also run across this issue on all three of the computers that I upgraded from 11.04 to 11.10.  On 2/3 machines, I have managed to fix it somehow.  On the third machine, I can't seem to make the message go away.  Following Old_Gray_Wolf's suggestion did not work for me either.

I have looked at some of your other posts. On the Ubuntu Forum, it is best to start your own thread explaining your problem rather that posting in an existing thread. I know that other Forums work differently and you get reprimanded for starting new threads; however, this is the Ubuntu Forum way of doing things. I am guessing that you haven't gotten a lot of answers to your problems for this reason.

---

### Post by scottku on 2011-10-25
The solution that I found was to remove the ia32-libs package and all of the packages that depend on it.  Then do the partial upgrade when prompted.  I'm not sure if subsequently reinstalling the packages that get removed with ia32-libs causes the problem to reappear or not---I didn't try that yet.  This fixed the problem on the last of the 3 machines that I encountered the problem on.

---

### Post by wmcbrine on 2011-10-29
Ubuntu Software Center won't even run. The icon blinks for a few seconds, then nothing.

I tried removing ia32-libs... no help.

---

### Post by Old_Grey_Wolf on 2011-10-30
Post the output of this command ```
cat /etc/apt/sources.list
```

---

### Post by wmcbrine on 2012-04-02
This finally resolved itself after an update the other day. Just in time for 12.04...

---

### Post by wmcbrine on 2012-05-04
...aaand it's back, in 12.04. :|

---

