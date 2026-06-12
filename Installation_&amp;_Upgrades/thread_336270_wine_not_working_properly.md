---
title: "wine not working properly"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by shadylookin on 2007-01-11
I recently had to format my Hard drive and reinstall ubuntu. I installed wine 9.29. however it doesn't add the .wine directory in my home folder so i don't get any of the necessary stuff to run windows applications.

 I tried to compile wine 9.28 (which always used to work) from source since i can no longer get it from the package manager(or at least i don't know how) and when runing the ./configure command it returned an error saying my compiler cannot create executables.

 is anyone else having this problem with wine 9.29 and is there a way to fix it?

---

### Post by arnieboy on 2007-01-11
try running the following command from terminal:
```
winecfg
```

---

### Post by shadylookin on 2007-01-11
that just brings up the configuration window. it doesn't add the necessary files or directories

---

### Post by arnieboy on 2007-01-11
> **shadylookin said:**
> that just brings up the configuration window. it doesn't add the necessary files or directories

have you checked lately?

---

### Post by shadylookin on 2007-01-11
when i run it i get this

```

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/shadylookin/.wine/drive_c', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

```

telling me what i already know(that the files weren't added)

then it brings up the normal configuration window.

---

### Post by arnieboy on 2007-01-11
> **shadylookin said:**
> when i run it i get this

```

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/shadylookin/.wine/drive_c', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

```

telling me what i already know(that the files weren't added)

then it brings up the normal configuration window.
alright try this:
```
rm -rf ~/.wine
```
and run ```
winecfg
``` again

---

### Post by beefcurry on 2007-01-22
ah great, that solve the problem for me. Thanks

---

### Post by Andreiz on 2008-03-23
thanks a lot this thread was usefull also for me

---

### Post by hjs1118 on 2008-05-15
it works for me, too. I can run steamapp with wine now.
very thanks.

---

