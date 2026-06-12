---
title: "How to do Ubuntu 12.04.2 LTS command-line fan control?"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by gharry on 2013-03-22
Running Ubuntu server 12.04.2 (brand new install) last night on the "Foxconn nt-A3700-0H0WBANA AMD A45 (Hudson D1) 1 x 204Pin AMD Radeon HD 6320 Black Mini / Booksize Barebone System" (just noticed that Newegg is giving away a free SSD drive with that - bummer).  Anyway, I have installed the lm-sensors package, run 'sensors-detect', and 'sensors' outputs:

```

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +64.0Â°C  (high = +70.0Â°C)
                       (crit = +100.0Â°C, hyst = +97.0Â°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +64.0Â°C


```

Running 'pwmconfig' gives me:

```

# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


```

The fan likes to spin up and down frequently (at roughly 64.5 degrees, it spins up, and then back down when the CPU temp reaches 64.0 again).  The system is idle 99% of the time.  The CPU temp seems high for a Linux box that's doing nothing.  The CPU is running in 'ondemand' mode:

```

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 825 MHz - 1.65 GHz
  available frequency steps: 1.65 GHz, 1.32 GHz, 825 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 825 MHz and 1.65 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 825 MHz (asserted by call to hardware).
  cpufreq stats: 1.65 GHz:3.51%, 1.32 GHz:0.58%, 825 MHz:95.90%  (581)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 825 MHz - 1.65 GHz
  available frequency steps: 1.65 GHz, 1.32 GHz, 825 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 825 MHz and 1.65 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 825 MHz (asserted by call to hardware).
  cpufreq stats: 1.65 GHz:4.69%, 1.32 GHz:0.25%, 825 MHz:95.06%  (467)

```

Any ideas?

---

### Post by 2F4U on 2013-03-22
Anything running in the background? Do you have a desktop installed? What graphics drivers are you using? By default, the open source ATI drivers have no power management configured. Is you graphics card active (i.e. with its own fan) or passive? A passive card may increase the temperature inside the case if the air flow is not adequate.

---

### Post by gharry on 2013-03-22
Oops!  Ubuntu *Server* 12.04.2 LTS.  Forgot the server part.  So, no GUI, very little in the background (just a OpenSSH server), and a VERY default Ubuntu install from CD.  So, I assume whatever graphics drivers come with Ubuntu Server, but does one really need graphics drivers for just terminal windows?

At any rate, I moved it a few feet further from me and I can't hear it now when the fan spins up.  Out of earshot, out of mind!  Still wouldn't mind a little better control of the fan but it isn't horrible as-is either.

---

