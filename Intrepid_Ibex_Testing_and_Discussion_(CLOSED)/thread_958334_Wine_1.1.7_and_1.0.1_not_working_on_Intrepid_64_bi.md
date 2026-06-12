---
title: "Wine 1.1.7 and 1.0.1 not working on Intrepid 64 bit - is Picasa the culprit?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nanonils on 2008-10-25
I can see Wine in my application menu but when I go to Programs/Acessories/Notepad nothing happens. I am unable to open the configuration nor am I able to uninstall using the Applications menu option.

I have Picasa installed. Upon searching around (how on earth do I get Google desktop to also search my file system, not just my home folder?) I found that Picasa has a Wine folder here: /opt/google/picasa/3.0

I uninstalled and installed 1.0.1, the stable version twice from the repositories using Synaptics without change - still not able to configure Wine. I then added the development packages of Wine to my software sources as described here, updated and reinstalled: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Still no luck.

When I use my system monitor to check for what processes open when I click e.g. notepad. Notepad and wineserver show for a second but then vanish. 

Should I remove Picasa to have Wine in the default directory? Will that remove my photos, etc? Is this a Picasa-Wine conflict?

I would very much appreciate your help! I always have to boot into Vista32 to run two key applications that I plan to install under Linux (Vector NTI and Powerpoint to have 1:1 rendering of the presentations of collaborators I have to occasionally work with (I use OpenOffice for my own)).

Thanks much!

---

### Post by nanonils on 2008-10-25
I guess Picasa is not the culprit. Removing it does not change a thing. After repeat install of Wine it still doesn't work. I'm totally lost. Why doesn't a fresh install after that via Synaptics fix it? When I now search for wine I find a large directory here: /usr/lib32/wine

If I run winecfg from the console I get:
laptop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
nils@nils-laptop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

Any help much appreciated!

---

### Post by YokoZar on 2008-10-26
Reinstalling from Synaptic won't do anything.  The broken Wine configuration will still be there.

Try removing or renaming your ~/.wine folder.

---

### Post by YokoZar on 2008-10-26
Also, and please give an honest answer, did you read the sticky thread?  I'm wondering if I need to reword the advice in there since I tried to answer this exact question.

---

### Post by nanonils on 2008-10-26
Yes, I did read both stickies but I made the mistake to use Synaptics's "mark for complete removal" option instead of manually fiddling with hidden files thinking that that would take care of it... well, it did not remove the files in .wine
Boy, a steep learnig curve indeed after coming from Windows... Thank you much for your fast response. This is invaluable in making the switch, lowering anxiety and spreading the word about Linux.
It is working now!

---

