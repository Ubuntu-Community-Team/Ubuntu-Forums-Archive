---
title: "Installation Help Needed"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by gtg on 2007-10-07
Have installed 7.04 successfully on two machines with CD.  However, when I try installation on my home desktop (3 year old HP Pavilion) I get dump-like error message immediately following the initial installation screen.  That is, two cryptic (to me) lines appear at the bottom of a VGA display:

Int 14: CR2 cf800000 err 00000000 EIP C020c3884 CS 00000060 flags 000100007
Stack: c00f7da0 c03f129b c0371d8c 00000002 c00f7da9 000f7da0 00000000 00000000

I just reinstalled WinXP on the machine from the same CD drive with no problems whatsoever.  Finally, memcheck indicates no problems with the 256 MB RAM installed.

Any help/suggestions would be most appreciated.

Thanks.

---

### Post by pay on 2007-10-07
Can you copy the messages before those?

---

### Post by gtg on 2007-10-07
That's what is at the bottom of the screen *immediately* after the very first selection screen (e.g., install ubuntu, install ubuntu in safe graphics mode, check CD, check memory, etc.).  Pick install or check CD, the screen momentarily goes blank, and then the lines listed appear with the computer "frozen" and requiring a power-off operation.

---

### Post by ddrichardson on 2007-10-07
Most HP machines require noapic option - select F6 from the menu and add "noapic" without the quotes and boot. Post back if it doesn't help

---

### Post by gtg on 2007-10-07
Thanks for the suggestion; however, the same error occurred.  :(

---

