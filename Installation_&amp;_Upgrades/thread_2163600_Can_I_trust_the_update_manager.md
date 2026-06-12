---
title: "Can I trust the update manager?"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by 00101010 on 2013-07-19
I would **REALLY and **rather stay with the 12.04 LTS last time I upgraded things didn't go so well. The question is can I "update" 12.04 without upgrading to 13.04. I feel afraid to run the update manager because I don't trust it to keep me at my current version and just install driver updates and what not. Is there a way around this? A way to know when ubuntu is updating or upgrading, A way to do it myself. A way to prevent it from happening. Anything, I would rather just go from LTS to LTS for stability.

---

### Post by ibjsb4 on 2013-07-19
If you have your package manager set to only upgrade to LTS versions, then you will not have any worries.

[ATTACH=CONFIG]244860[/ATTACH]

Or you could take it a step further and use [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") and choose which updates/versions you want.

```
sudo apt-get install synaptic
```

---

### Post by QIII on 2013-07-19
Hello!

The commands

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

and

```
sudo apt-get dist-upgrade
```

all work within the context of your current version.

The last one often confuses people.  It does not upgrade you to the next version.  It is the same as the second command, with the exception that it will install kernel upgrades for your current version and update you to new versions of software as it can while intelligently attempting to keep dependencies sorted out.

I just use the first and third commands all the time.

The command to upgrade to a new version is completely different.

Cheers!

---

### Post by deadflowr on 2013-07-19
> [COLOR=#000000]The question is can I "update" 12.04 without upgrading to 13.04.[/COLOR]

Yes.
Just don't click the new version available "Upgrade" button.
If the newer version button is bothersome, go to the setting button and click it.
Then when the software sources box opens go to updates.
Then go to notify when new release and change the setting there from whatever it is to something else(preferably long-term-release only)
When you've set that, close the software sources window and then in the update manager click "check".
Check will run the package updating command, and when done, the Upgrade option won't be there.(If it ever was)

To install normal updates, per 12.04, just click the install updates button in the button right corner.
Updates for the current version are always in the bottom, where as Upgrade options are always at the top.

---

### Post by bmavbeard on 2013-07-19
I am happy.  I think I might can help here but I will give a forewarning I am a noob big time.  

I was thinking the same thing because I have 12.04 and I am not trying to update to a new version.  When you pull up update manager (However you do it I only know to search in Dash) you can look on the bottom left at the tab that says settings.  Click it and you will have to put in your password.  

Go to the tab that says updates.

At the bottom it says "Notify me of a new Ubuntu version (I have that set to "For long-term support versions")  You can set it to "for any new version" or you can set it to "never"

If you are really adamant on not updating past 12.04 you can set this to never.  If you want to only update to LTS set it to long term support versions.  If you want to update every time a version comes out set it to any new version.

If I where you I would set it to LTS versions but that is up to you.

Once you do that you can "trust" update manager not to go past 12.04.

I really hope this helps. I am a complete noob and I want to be able to help other people.

---

### Post by Buntu Bunny on 2013-07-19
> **QIII said:**
> Hello!

The commands

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

and

```
sudo apt-get dist-upgrade
```

all work within the context of your current version.

The last one often confuses people.  It does not upgrade you to the next version.  It is the same as the second command, with the exception that it will install kernel upgrades for your current version and update you to new versions of software as it can while intelligently attempting to keep dependencies sorted out.

I just use the first and third commands all the time.

The command to upgrade to a new version is completely different.


QIII, thank you for that explanation. I've committed myself to learning and using the command line more, and thought as you said about the third command. The information is appreciated.

---

