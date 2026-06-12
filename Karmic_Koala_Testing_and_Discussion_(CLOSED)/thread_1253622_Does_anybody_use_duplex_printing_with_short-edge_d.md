---
title: "Does anybody use duplex printing with short-edge duplexing?"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-30
Among other gifts CUPS 1.4.0 has prepared for us I have found this one:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459)

Has anybody an appropriate printer to confirm the issue?

---

### Post by ilna on 2009-09-02
Now, when these

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797)

bugs are really fixed (thanks to the team!), I'd want to re-ask this thread question. Am I the only owner of a printer with duplex printing among all those brave Karmic testers? Can not believe! :)

If I'm not alone here, can anybody verify short-edge duplexing really work (or doesn't work, and confirm [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459) )?

To test, only two very simple steps are needed:

1. "Print" (via any app with 'Print' in menu) any **two** pages to postscript file (say, you have named this file as 12.ps),

2. really print this pages to your printer:

```
lp -d FS-1030D -o media=A4 -o sides=two-sided-short-edge 12.ps 
```

Here replace 'FS-1030D' with your printer's name.
Please, help! The issue is a real show-stopper for me.

---

