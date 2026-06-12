---
title: "wine error running a 16bit software for windows"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by lezich on 2007-12-19
Hi, i've installed the last version of wine
wine-0.9.46
i can start running the software, but when i trying to open the windows that i ca charge the data, i got the message below, i already configure for win95, win98, 3.1, 2000, xp and nothing works.

when i use this command
wine soft.exe, i get this error

[B]00000 file = /home/lezich/.wine/dosdevices/g:/SISTEMA/SYS2/WIN/TANGODSP.FON
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 00000000 file = /home/lezich/.wine/dosdevices/g:/SISTEMA/SYS2/WIN/TANGODSP.FON
fixme:font:WineEngCreateFontInstanceUnhandled exception: wait failed on critical section 0x7b9274c0 Win16Mutex
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39110
lezich@PC:~/MONDIAL/SISTEMA/SYS2/WIN$ Process of pid=000a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000d 
        0000000f    0
        0000000e    0
No process loaded, cannot execute 'detach'

---------

when i use this command
WINEDEBUG=-all wine soft.exe

i get this error (almost the same)

wine: Critical section 7b9274c0 wait failed at address 0x7bc39110 (thread 000c), starting debugger...
Unhandled exception: wait failed on critical section 0x7b9274c0 Win16Mutex
lezich@PC:~/MONDIAL/SISTEMA/SYS2/WIN$ Process of pid=000a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
No process loaded, cannot execute 'detach'


-------------------------------------------------------------------
[/B]


i need to run this program to migrate to ubuntu
thanks for the help

---

