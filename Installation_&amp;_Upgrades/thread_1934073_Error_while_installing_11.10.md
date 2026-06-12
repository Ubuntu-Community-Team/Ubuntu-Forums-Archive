---
title: "Error while installing 11.10"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by ktolsen on 2012-03-01
I tried to install Ubuntu 11.10 through Wubi last night, but when I rebooted the machine as prompted I was given a long strand of code, the last few seemed like errors. They were:

[   87.452935] Bad LUN (0:1)
[   87.472378] Bad target number (1:0)

It had a few more lines of bad target numbers, followed by a persistent black screen. 

Thanks for the help.

---

### Post by Paddy Landau on 2012-03-02
I see no one has answered you. I'm no expert in WUBI, but I do know that WUBI often suffers from installation problems.

Can you boot into Windows?

If you can, please uninstall WUBI; download Ubuntu and burn to a CD or USB; boot from the CD or USB; choose "Try Ubuntu" (it will not change anything on your computer); and check whether or not it works. Let us know.

If you cannot boot into Windows, please post back here and I hope someone more knowledgeable than I will help.

---

### Post by ktolsen on 2012-03-02
thanks for the reply, I can log into windows so I'll try this and reply back as soon as I attempt your  suggestion.

---

### Post by ktolsen on 2012-03-02
I put 11.10 on a USB drive, and when I booted into it the startup menu appeared. I selected to try it on the USB, but after about a page of code, it ended up as a black screen again. I waited a while and all that happens at that screen is what sounds like the sound that plays when a system boots up, even though it's still a black screen.

---

### Post by Paddy Landau on 2012-03-03
This means that there is a driver problem. The startup sound plays, so it indicates that Ubuntu is unable to recognise your monitor.

Search these forums for your particular computer model in case someone else has managed to solve your problem.

Also post your model here in case someone who knows about it reads this thread and can help. If you can include your specifications including your graphics card, that may help.

---

### Post by alkh3myst on 2012-03-03
Another possibility is that you may have corrupted part of your Windows filesystem, with the attempted install and uninstall of ***Wubi*** (I hate using four-letter words like w___). Wubi is a horrible mistake that needs to be buried in a deep hole somewhere. Along with checking the drivers, as Mr. Landau recommends, you may want to install Ccleaner in Windows, run the cleaner, and *then scan and repair the registry*, if necessary. Wubi is evil, evil, evil. I think I saw on a forum that it was created by demons.

---

### Post by Paddy Landau on 2012-03-03
> **alkh3myst said:**
> Another possibility is that you may have corrupted part of your Windows filesystem...
Possible, but unlikely; as [post=11733850]the OP said[/post], even the Live CD has this problem.

> **alkh3myst said:**
> Wubi is a horrible mistake ... it was created by demons.
[Laughing] It's wasn't such a bad mistake. WUBI was the tool that allowed me to experiment with Ubuntu (before the days of persistence on a Live USB) and thus gave me the courage to create a full installation and ultimately leave Windows.

Having said that, I do agree that the time has come to peacefully put WUBI to rest now that Ubuntu can run from a Live USB with persistence...

... Unless the developers can solve the recurrent flaws with WUBI (which I don't suppose will happen).

---

