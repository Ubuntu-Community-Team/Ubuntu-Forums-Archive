---
title: "Help installing AVG anti-virus"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by sharkins215 on 2010-09-09
Hello all,
      so i've been trying to install AVG on my computer for some time now and have exhausted nearly every option in the DIY section i turn to you :) i'm very new to ubuntu so i'm hoping i'm making a rookie mistake here but here's what i've done so far. I've downloaded the installer from avg with the extension .deb. That opened up in the package manager and the installation went off without a hitch. Then i went to find the application but it is nowhere to be found. So i tried restarting thinking that maybe it needed that but even after the restart i still couldn't find it anywhere. so i tried reinstalling it and still no luck. Any help you guys can give me would be greatly appreciated :) Thanks

---

### Post by realzippy on 2010-09-09
Do you want to scan windows machines or data for windows machines?

If not,there should be no need for a antivirustool....and welcome to the forum!

---

### Post by sharkins215 on 2010-09-09
Well i'm actually running ubuntu on a virtual machine so i want the protection on both ends

---

### Post by realzippy on 2010-09-09
Applications > Accessories > AVG   ??

---

### Post by realzippy on 2010-09-09
Try to start it from terminal.

```
sudo avgctl --start
```

---

### Post by sharkins215 on 2010-09-09
ok i did that and it said the operation was successful but i still don't see it anywhere.... lol

---

### Post by howefield on 2010-09-09
There is no GUI with AVG for linux, it is a command line anti virus scanner.

If you want point and clicky, try Avast or, in my opinion, the best which is Bitdefender for Unices, both have .deb packages for download also.

---

### Post by realzippy on 2010-09-09
[https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)


...maybe it is outdated.

---

### Post by howefield on 2010-09-09
> **realzippy said:**
> [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)


...maybe it is outdated.

No maybe about it. It is outdated.

I think it was 8.5 onwards that AVG for linux had no GUI. It is a regular topic on these forums with many threads available for the OP to search out...

You either learn to run AVG from the command line, or ditch it and get another, Avast for example, or BitDefender.

---

### Post by sharkins215 on 2010-09-09
oh ok thanks guys. That makes alot more sense to me. What doesn't make much sense is why they would ditch their gui but hey i guess that their decision to make. Anyways thanks a bunch :)

---

### Post by uRock on 2010-09-09
They would have to invest time into creating a GUI that very few would be using. If you want an AV with a GUI, then ClamTK works well.

---

### Post by sharkins215 on 2010-09-09
oh sorry one more thing. Assuming AVG installed correctly to my computer how would i go about removing it if i can't see it?

---

### Post by uRock on 2010-09-09
It should be listed in System> Administration> Synaptic Package Manager after being installed, but I could be wrong.

---

### Post by sharkins215 on 2010-09-09
AH! thank you very much good sir :) i was looking in the ubuntu software center in the installed software section.

---

### Post by kavulix on 2010-12-31
If you're looking for a gui for avg or any other linux AV scanner you can use the Penguin Pills application.  The scan/update paths and options window can be customized to support any CL scanner.  I'd recommend reading through the entire page below before using it for the first time.

[http://penguinpills.sourceforge.net](http://penguinpills.sourceforge.net)

---

