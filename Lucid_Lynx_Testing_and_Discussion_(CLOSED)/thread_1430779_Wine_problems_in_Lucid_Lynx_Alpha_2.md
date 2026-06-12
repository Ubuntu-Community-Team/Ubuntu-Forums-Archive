---
title: "Wine problems in Lucid Lynx Alpha 2"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fremantle on 2010-03-15
Whenever i try to open a .exe with the latest wine this error comes up..>>
> The file '/home/abir/Downloads/Firefox Setup 3.6.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
in here i tried to install firefox windows version


any solutions?

---

### Post by prodigy_ on 2010-03-15
> **fremantle said:**
> any solutions?
```
chmod +x /home/abir/Downloads/Firefox\ Setup\ 3.6.exe
```

---

### Post by Lucretius on 2010-03-15
right click and tick the "allow to run as a program" box

---

### Post by GeoPirate on 2010-03-15
curious, why would you run the windows version of firefox in wine instead of just running the linux version?

---

### Post by executorvs on 2010-03-16
there are several reasons. the one I've had most frequently is websites which require use of activex and while it takes work to get activex running in wine it can be done. other problems can be .Net, Silverlight 3.x, and macromedia shockwave as it's code isn't read by shockwave flash in many cases.
It's the same reason I have been trying to iron out use of IE in wine.. some websites are just built with intended dependence on M$ components.

I'm down to two websites I haven't been able to find work arounds for in linux:
1. netflix.com (I think I'm almost there for streaming video in wine though)
2. nom.Mlxchange.com (same as above)

all the former reasons I did this I have since found solutions for in linux builds of firefox.

---

### Post by fremantle on 2010-03-21
theres a website called *******.com. Its videos dont work on linux firefox

---

### Post by fremantle on 2010-03-21
i also tried other .exe Doesnt work.

---

### Post by nu2linux6 on 2010-03-21
It's part of the new security policy in Lucid. Windows executables won't run unless the execute bit is set.

[https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required]("https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required")

---

### Post by littlesatan on 2010-03-25
Oh, Security. Nice.
Can anybody explain, how to set execute bit to a .exe from mounted ISO file?

---

### Post by littlesatan on 2010-03-25
> Applications, including desktops and shells, must not run executable  code from files when they are both:  
[LIST]
[*]lacking  the executable bit
[*]**located  in a user's home directory or temporary directory. **
[/LIST]
I move my file.iso to /usr/*, then mount and all works fine.

---

### Post by bohemier on 2010-04-19
I wasn't able to make it work... I use Archive Mounter on the iso then I open the mounted iso and execute the exe file with wine. Moved the iso file to /usr, /usr/bin but I still get the executable bit error when trying to execute setup.exe inside the iso. 

Does anyone know a way to solve this?  (besides extracting the whole iso and marking the exe file as executable!)

Is this new policy configurable?

p.s.: Using 10.04 beta 2

---

