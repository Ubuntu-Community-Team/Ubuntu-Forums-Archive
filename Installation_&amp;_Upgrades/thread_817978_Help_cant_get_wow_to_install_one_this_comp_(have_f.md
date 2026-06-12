---
title: "Help cant get wow to install one this comp (have followed directions)"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by zann00000 on 2008-06-04
I have successfully been able to install wow on my desktop computer and it work fine (some weird graphic flaws but fine all the same). However i went to install wow on my laptop and have run into a nightmare. First i installed every thing got some weird errors on the control panel 

zann00000@zann00000-laptop:~$ cd //home/zann00000/Desktop/woow
zann00000@zann00000-laptop://home/zann00000/Desktop/woow$ wine Installer.exe
err:wineboot pendingRename couldn't get file attributes (3)
err:wineboot pendingRename couldn't get file attributes (3)
err:wineboot pendingRename couldn't get file attributes (3)
err:wineboot pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (3)
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:powrprof:DllMain (0x7e200000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e200000, 0, (nil)) not fully implemented
fixme:font:CreateScalableFontResourceW (1,L"C:\\windows\\temp\\Blizzard Installer Temporary Data - 0069a6e0\\FrizQuadrata.fot",L"C:\\windows\\temp\\Blizzard Installer Temporary Data - 0069a6e0\\FrizQuadrata.ttf",(null)): stub
zann00000@zann00000-laptop://home/zann00000/Desktop/woow$
zann00000@zann00000-laptop://home/zann00000/Desktop/woow$


It finally did come up after taking a bit and i started the download. Once it was done i clicked to start it up. Just like on my desktop when i first started it, it starts black and has an error so i closed it and just like on my desktop it had shifted my graphics a bit, but unlike on my desktop when I clicked to restart it all it did was go through the two entry movies making the first sounds of the login screen music and then just kind of faded away with every thing black till i moved my curser over it witch made my back screen come into view.

Their is a second part to this confusion. I then had a friend who wanted to try to fix it. He tried to unload the game by first going to the c:/ files and deleted the wow file. then he unloaded it using the wine unload thing. I restarted my computer and it was still their so in frustration i tried getting rid of wine. But even though wine is gone it still shows it their with wow sitting thing but with no files to back it up. Any ways it is incredibly important to me to get this going and i would immensely be thankful for anyones insight.

---

### Post by iaculallad on 2008-06-04
You could try re-installing wine first by getting it [here]("http://wine.budgetdedicated.com/archive/index.html"), then run the command **wineprefixcreate** 

Or just try executing this command and redo your installation:

```
wineprefixcreate
```

---

### Post by zann00000 on 2008-06-04
> **iaculallad said:**
> You could try re-installing wine first by getting it [here]("http://wine.budgetdedicated.com/archive/index.html"), then run the command **wineprefixcreate** 

Or just try executing this command and redo your installation:

```
wineprefixcreate
```

I did that but allas wow still shows up when i look in the wine programs even though it has no files to back it.

---

### Post by zann00000 on 2008-06-04
OK so i reinstalled wow and it seemed to fix every thing with wine missing files and stuff but still when i go to play it, it does the intro movies makes the sound of the home screen and then terminates itself. Please please help

---

