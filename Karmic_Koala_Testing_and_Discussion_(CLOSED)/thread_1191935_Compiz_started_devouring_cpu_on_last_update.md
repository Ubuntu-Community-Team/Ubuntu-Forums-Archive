---
title: "Compiz started devouring cpu on last update"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-06-19
Hello all,

I run karmic 32-bit with x1600 ati card, using the free radeon driver.

After last update to compiz, it started eating up cpu. The system monitor and 'top' command report the two cpu's are working on around 50% cpu load each. Weirdly, the compiz process itself does not report excessive cpu usage, but when I kill it the cpu goes back to normal. The compiz command does not give any error messages.

I have tried disabling all compiz plugins and switching configuration backends, but to no avail.
Relevant sections of my xorg.conf are:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option 		"AccelMethod" "EXA"
#	Option 		"MigrationHeuristic" "greedy"
        Option 		"EnablePageFlip" "on"
        Option          "ColorTiling"   "on"
      	Option      	"AGPFastWrite" "yes"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
	Load "vbe"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "int10"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
	Option "DAMAGE" "Enable"
	Option "RENDER" "Enable"
EndSection

Section "ServerFlags"
   	Option "AIGLX" "true" 
	Option "DontZap" "false" # enable ctrl+backspace x reset
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection
```

Any ideas how to tackle this?

---

### Post by psyke83 on 2009-06-19
Yes - try with a bare configuration to isolate potential problems. The migration heuristic varies a lot depending on the driver - for example, in Intrepid the "greedy" migration heuristic was always fast for me with the Intel driver, but setting "ExaOptimizeMigration" to true and "MigrationHeuristic" to "always" was better, especially for compiz.

There are other radeon options you should check via "man radeon" too.

---

### Post by Wise Ferret on 2009-06-19
I tried bare configuration with no option set under X's device section, but it did not help. I did not find any relevant option in radeon's man page.
Anyway, this problem is only 2 or 3 days old. Compiz worked well until now. Any ideas on how to start to debug this?

---

### Post by psyke83 on 2009-06-19
Did you try with a bare configuration and ExaOptimizeMigration set to true? Don't mix it with the "greedy" "MigrationHeuristic".

Also look at a recent changelog: [https://lists.ubuntu.com/archives/karmic-changes/2009-June/002215.html](https://lists.ubuntu.com/archives/karmic-changes/2009-June/002215.html)

If that doesn't help, perhaps change the "AccelMethod" back to the old XAA architecture?

In Section "Device":
```

Option "AccelMethod" "xaa"

```

Check your log to ensure that XAA gets enabled correctly, though.

---

### Post by Nossile on 2009-06-19
> **Wise Ferret said:**
> Hello all,

I run karmic 32-bit with x1600 ati card, using the free radeon driver.

After last update to compiz, it started eating up cpu. The system monitor and 'top' command report the two cpu's are working on around 50% cpu load each. Weirdly, the compiz process itself does not report excessive cpu usage, but when I kill it the cpu goes back to normal. The compiz command does not give any error messages.

Any ideas how to tackle this?


On my machine is the same, but I use an geforce 8600gs with proprietary drivers.

---

### Post by Wise Ferret on 2009-06-19
> **psyke83 said:**
> Did you try with a bare configuration and ExaOptimizeMigration set to true? Don't mix it with the "greedy" "MigrationHeuristic".

Also look at a recent changelog: [https://lists.ubuntu.com/archives/karmic-changes/2009-June/002215.html](https://lists.ubuntu.com/archives/karmic-changes/2009-June/002215.html)

If that doesn't help, perhaps change the "AccelMethod" back to the old XAA architecture?

In Section "Device":
```

Option "AccelMethod" "xaa"

```

Check your log to ensure that XAA gets enabled correctly, though.

Thank you for your efforts.
I have tried using xaa, and after that - exa with ExaOptimizeMigration set to true. Both did not solve the problem.

---

### Post by Wise Ferret on 2009-06-19
The problem persists with radeonhd.
I deduce that this is a compiz bug.

A bug report has been filed: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/389686](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/389686)

---

