---
title: "upgrade 10.4 boot problems"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by lapis72 on 2010-05-16
hi all upgraded to 10.4 from 9.10 , now can only boot in low-res mode. Only a newbie so don't know how to fix it

---

### Post by Catharsis on 2010-05-16
What graphics card do you have?
```
lspci | grep VGA
```

---

### Post by lapis72 on 2010-05-16
sorry could not get the code to work , typed "lspci / grep Vga" just list some command options

---

### Post by CTBuckweed on 2010-05-16
The '|' is a pipe directive. It feeds the output of the 1st command to the input of the 2nd command.

lspci | grep VGA --- looks for the string 'VGA' in the output of lspci and prints only those lines that match the string search. lspci outputs many lines of data regarding the system devices.

---

### Post by Catharsis on 2010-05-16
You can just copy-paste it into the terminal. Just remember that the terminal needs an additional Shift (i.e. Ctrl+Shift+v for paste) if using keyboard shortcuts.

---

### Post by garvinrick4 on 2010-05-16
> **lapis72 said:**
> hi all upgraded to 10.4 from 9.10 , now can only boot in low-res mode. Only a newbie so don't know how to fix it
Do you mean the boot screen is in low-res?

If that is problem

```
sudo apt-get install startupmanager
```It will be in Administration and you can change it to 4 or 5 different ones there.

If you can only boot in low-res to you have to start looking into card and drivers issues. Follow previous advice.
This below will give you all your cards and drivers just save it somewhere so you always have it handy. 

 lspci -v | less

---

### Post by lapis72 on 2010-05-16
should also clarify can only boot in "failsafe graphics mode" in the recovery kernell

---

### Post by lapis72 on 2010-05-16
here the result

       Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Toshiba America Info Systems Device 0033
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff8 [size=8]
        Capabilities: <access denied>
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Toshiba America Info Systems Device 0033
        Flags: fast devsel
        Memory at 20000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at 2c000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1440 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1460 [size=32]
        Kernel driver in use: uhci_hcd

---

### Post by Catharsis on 2010-05-16
You're suffering from a known issue with intel 855 graphics cards. Please see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by lapis72 on 2010-05-16
thanks for the link , this has resolved my boot issue !

---

### Post by garvinrick4 on 2010-05-16
lapis72 here needs a little help I have never looked into this problem nor had it, give him a helping hand please.
He has solved earlier. My mistake.

---

### Post by Catharsis on 2010-05-16
> **lapis72 said:**
> thanks for the link , this has resolved my boot issue !

Glad to hear it worked for you :). Do you mind marking this thread as solved by clicking "Thread Tools" at the top? Thanks.

---

