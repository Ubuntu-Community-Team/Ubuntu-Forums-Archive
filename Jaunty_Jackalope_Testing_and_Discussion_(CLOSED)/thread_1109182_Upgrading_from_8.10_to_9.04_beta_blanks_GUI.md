---
title: "Upgrading from 8.10 to 9.04 beta blanks GUI"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cajunaggie on 2009-03-28
I have no GUI functions at all.
*Warning: Info Dump ahead:*
Yesterday I used the upgrade manager to upgrade from Ibex to the Jaunty beta. I got no error messages other than prompts to replace "custom" files with new ones. Having had problems in the past if I didn't replace them, I replaced the "custom" files. Unfortunately I don't remember what they were.

After a reboot, I received an error message saying that Ubuntu could not recognize my graphics settings. I attempted to continue with the "continue with low-graphics" option, but that brought up a blue sceen with an error message saying there was already a copy of x-server running on 0:, with the option to try running X-server on a higher console using Alt+Ctrl+F$. I ran through all twelve function keys with no response. 

There were also options to drop into console mood, reconfigure graphics settings, and review graphics log. I'm not particularly skilled with the last two so I dropped into console mood thinking there might be an update or a patch that fixes this. 

I rebooted and dropped into console mood using line commands to update/upgrade as many packages as I could, logging out and logging in after each update until there were no new remaining packages. When logging in through the command line I did notice a message saying there was "1 zombie process running". Also, when booting I'll also notice a repeating set of four lines:
```
ath5k phy0: noise floor cancellation failed 2417 MHZ
ath5k phy0: noise floor cancellation failed 2422 MHZ
ath5k phy0: noise floor cancellation failed 2427 MHZ
ath5k phy0: noise floor cancellation failed 2432 MHZ
``` with each line being preceded by what I'm assuming is an event number.

I trying running the Jaunty Beta LiveCD with the same results, though I haven't tried running earlier versions of the LiveCD (8.10, 8.04 etc)

Is this a common problem? Does anyone have any ideas on how to work around this?

---

### Post by cajunaggie on 2009-03-28
I just realized that I posted this in the wrong forum. Would one of the mods be so kind as to move this?

---

### Post by cajunaggie on 2009-03-28
Update:
After running "Fix Broken Packages" in the recovery kernel, I am now able to get a GUI going through the low-graphics mode. It keeps telling me "0: is busy, so X will run on 1:" and the processor load reads 100% constanstly, but at least I'm able use it again.

---

