---
title: "Hello, apology from my English..."
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2016-01-26
Hello, apology from my English...
I have install a new version Ubuntu in 64 bit machine and I have install Skype according to your instructions, but I try to set Greek language, I see, but I cannot see after  "En" upper right the "Gr". 
Also have happened all updates, but always I see "Install updates", I  press but always I see it is ok with Updates, I wait for your answer, thanks a lot...

---

### Post by Vladlenin5000 on 2016-01-26
Skype should pick up the OS language. Have you set it at Language support (also advisable to set the correct locale at Regional Formats in the same dialog)?

Regarding updates please do this sequence of commands, one by one, in the terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If any, please post here the complete error messages.

---

### Post by spi2 on 2016-01-26
hello [COLOR=#000000][FONT=Helvetica Neue]Vladlenin5000,

thanks, ok with updates...

but Skype I select English language, [/FONT][/COLOR]and what you mean: (also advisable to set the correct locale at Regional Formats in the same dialog)? I think is the same...

what else can I do?

---

### Post by Nuno_Abreu on 2016-01-26
It should be in the System Settings application - is that one you're referring to?

---

### Post by Vladlenin5000 on 2016-01-26
The suggestion was to change to Greek and apply at the OS level (System Settings > Language Support) and mentioned the Regional Formats because they're independent settings and people often forget about this details.
Skype by default picks the OS language (if available). Unfortunately for you Skype for Linux doesn't support Greek so it will default to English as usual. I thought it did but checked on mine and surprisingly it doesn't. As such there's nothing you can do.

---

### Post by grahammechanical on 2016-01-26
> I see, but I cannot see after  "En" upper right the "Gr".
Is this in the Skype Window or in the top panel of Ubuntu?

The icons we see on the right of the top panel in Ubuntu are called app indicators. The icon that is the letter En is the keyboard layout app indicator. In the drop down menu we can select Text Entry Settings and we will get a dialog that will allow us to add or remove keyboard layouts. We click the Plus ( + ) icon to add a new keyboard layout from a list of different language keyboard layouts. There are four in the list for the Greek Language.

After doing this we will see the new keyboard layout appear in the drop down menu of the keyboard layout app indicator. And we can change from one keyboard layout to another by selecting the new keyboard layout. The change in keyboard layout should work in all applications but I have not tested this with Skype.

Regards.

---

