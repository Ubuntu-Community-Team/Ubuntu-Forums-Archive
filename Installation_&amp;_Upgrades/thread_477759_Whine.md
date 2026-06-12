---
title: "Whine"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by crxvfr on 2007-06-18
I'm pretty good with computers but ubuntu makes me feel stupid.

I just installed wine. Lots of the posts I've read said thats all they needed to do to run windows apps. Sounds easy enough. I installed it.

After discovering everything I just installed was hidden, I moved the app I wanted to run to .wine/c_drive, then added it, an install exe, in winecfg. I then ran "wine myapp" and it appeared to install. Groovy, I'm thinking. I wonder where it is?

I do SU and get root privileges but still can't see the "Program Files" dir after doing LS in terminal???

In the filebrowser, I **can** see and get to this dir and Program Files too, but still no installed program.

I couldn't find it so I installed it again. It says it installed the app in "Program Files".  Program Files is empty.

Why does it feel like my common sense failing me? Maybe its the nature of the questions I have to ask that make me feel so stupid.

Where is the program I just installed? If I knew where it was, I could run it, theoretically.
```
root@joe-desktop:/home/joe/.wine/drive_c# wine LSTerm32Setup_2[1].0.0.16IP.exe
wine: creating configuration directory '/root/.wine'...
wine: '/root/.wine' created successfully.
fixme:ntdll:NtQuerySecurityObject (0x70,0x00000007,0x521758,0x00007800,0x33e8f8) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
root@joe-desktop:/home/joe/.wine/drive_c# winecfg
root@joe-desktop:/home/joe/.wine/drive_c# ls
LSTerm32Setup_2[1].0.0.16IP.exe  Program Files  windows
root@joe-desktop:/home/joe/.wine/drive_c# cd program Files
bash: cd: program: No such file or directory
root@joe-desktop:/home/joe/.wine/drive_c# cd Program Files
bash: cd: Program: No such file or directory
root@joe-desktop:/home/joe/.wine/drive_c# cd windows
root@joe-desktop:/home/joe/.wine/drive_c/windows# wine notepad.exe
root@joe-desktop:/home/joe/.wine/drive_c/windows# cd ..
root@joe-desktop:/home/joe/.wine/drive_c# wine LSTerm32Setup_2[1].0.0.16IP.exe
fixme:ntdll:NtQuerySecurityObject (0x70,0x00000007,0x521768,0x00007800,0x33e8f8) stub!
fixme:ntdll:NtQuerySecurityObject (0x78,0x00000007,0x521768,0x00007800,0x33e8f8) stub!
fixme:ntdll:NtQuerySecurityObject (0x78,0x00000007,0x521768,0x00007800,0x33e8f8) stub!
fixme:ntdll:NtQuerySecurityObject (0x78,0x00000007,0x521768,0x00007800,0x33e8f8) stub!
fixme:ntdll:NtQuerySecurityObject (0x78,0x00000007,0x521768,0x00007800,0x33e8f8) stub!
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

root@joe-desktop:/home/joe/.wine/drive_c# ls
LSTerm32Setup_2[1].0.0.16IP.exe  Program Files  windows

root@joe-desktop:/home/joe/.wine/drive_c# cd Program Files
bash: cd: Program: No such file or directory

root@joe-desktop:/home/joe/.wine/drive_c# cd Program_Files
bash: cd: Program_Files: No such file or directory

root@joe-desktop:/home/joe/.wine/drive_c# cd ./Program Files
bash: cd: ./Program: No such file or directory

root@joe-desktop:/home/joe/.wine/drive_c# cd ./Program_Files
bash: cd: ./Program_Files: No such file or directory

root@joe-desktop:/home/joe/.wine/drive_c# 
```

Searching for "fixme:ntdll:NtQuerySecurityObject" in Google returns a whopping 8 results.

---

### Post by dfreer on 2007-06-18
The problem here is that you should be using this command:
```
cd Program\ Files/
```
You need to escape the whitespace in the folder name with the "\"

One tip for new users with the terminal is to use the <Tab> key. You could start typing
```
cd Pro
```
Then hit the <Tab> key. If there is only one file/command that starts with "Pro", it will automatically fill in the required field like so:
```
cd Program\ Files/
```
If there are more than one files that begin with "Pro", it will make a system beep. Upon hitting the <Tab> key one more time, it will show you all of the files that begin with "Pro"

Another tip would be to open the File Browser Nautilus, hit <Ctrl>+<h> to show hidden files (those beginning with a .*), and then navigating to the program files directory to view whatever program you are trying to install. Note that not all programs will work with wine, check with winehq if your program does not work and see if there are any known issues with it. Good luck and welcome to Ubuntu!

---

### Post by crxvfr on 2007-06-18
Thanks!
I tried underlines.
As much work as I've done on the web, I didn't think about escaping it.

btw, Crossover Office worked flawlessly on a friends computer, installing and running the same program, which requires a security hasp to run! Maybe I'll just dish out the dough till I get better, one tip at a time. I've been 20 years at windows and I'm 44. Oh No! I hope I can get this stuff down before I'm 60. :)

---

### Post by dfreer on 2007-06-18
You're Welcome! Yeah, it's a bit misleading because ls -l displays with non-escaped whitespaces.

---

