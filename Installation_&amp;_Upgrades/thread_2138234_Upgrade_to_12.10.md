---
title: "Upgrade to 12.10"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by skhozema on 2013-04-23
I upgraded to 12.1 from 12.04. I would like to know during the process and after upgradation when i opened Synaptic Package Manager, under settings- Repository- Other Software list various files which were disabled while upgrading. Should these files to be deleted or is it to enabled and if so how. :confused: Also attached pic for the same ..

---

### Post by PowerBarry43 on 2013-04-23
Hi

When you perform a release upgrade any extra repos that you've added yourself get disabled. I'm guessing this is to prevent any confilcts for example packages with the same name in two different repos that may have different dependencies. Basically just to be a known stable state during the upgrade. Things like the handbrake repo theres no harm in enabling again which you can do just by ticking the box at the start of the line then pressing OK.

Hope this helps!

Barry

---

### Post by skhozema on 2013-04-23
> **PowerBarry43 said:**
> Hi

When you perform a release upgrade any extra repos that you've added yourself get disabled. I'm guessing this is to prevent any confilcts for example packages with the same name in two different repos that may have different dependencies. Basically just to be a known stable state during the upgrade. Things like the handbrake repo theres no harm in enabling again which you can do just by ticking the box at the start of the line then pressing OK.

Hope this helps!

Barry

Thanks Barry for your quick reply, As adviced i checked the box but there is no option for OK ... If you check the previous pic again which i had attached there are option choices as ADD,EDIT, REMOVE. If chose edit the window open pic is as attached.. stuck again.. 

[ATTACH=CONFIG]241683[/ATTACH]

from this point how to go :confused:

---

### Post by PowerBarry43 on 2013-05-09
Hi again

sorry an OK button isn't needed I meant to say close. Just ticking the box and pressing close is sufficient to enable the repo. You also want to edit the name of the source and remove the "Disabled on upgrade" part to avoid future confusion! After that just run:

```
sudo apt-get update
```

And check that the sources appear in the output to confirm that it's worked! ;)

Hope this helps!

Barry

---

