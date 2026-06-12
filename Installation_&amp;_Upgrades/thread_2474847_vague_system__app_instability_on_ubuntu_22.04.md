---
title: "vague system? / app instability on ubuntu 22.04"
date: 2022-05-09
forum: Installation &amp; Upgrades
---

### Post by bingodingo on 2022-05-09
I have some vague instability with mostly browsers (firefox, chrome) - random crashes, freezes, instability.
Not sure if it's the apps or the system.
The following syslog entry maybe associated with one of the app crashes:
May 10 12:35:29 ...  firefox[2604] The program 'firefox' received an X Window System error.#012This probably reflects a bug in the program.#012The error was 'BadValue'.#012  (Details: serial 1275429 error_code 2 request_code 53 (core protocol) minor_code 0)#012  (Note to programmers: normally, X errors are reported
Vague, intermittent instability seems to persist after a reboot.
Have updated / upgraded everything this am.

Searching in the activities search bar also apparently causes the gnome shell to crash sometimes.

Starting to think it might be less work to  go back to 20.04. 
22.04.01 will obviously be more stable, but in many years of early adopting LTS releases I don't recall having so much trouble before.

Context:
Clean install about a week ago of Ubuntu 22.04. (20.04 previous ran well on this system).
Multiboot system (Ubuntu only on this drive, Windows 10 on another, Windows 10 runs fine).
Hardware: i9 9900k, Radeon 6800x, Z390-AORUS-PRO-WIFI (F12 bios), SSD, using ethernet (not wifi), hardware TPM, secure boot and other annoying bios settings OFF.

Thanks

---

### Post by Holger_Gehrke on 2022-05-10
On my XUbuntu 22.04 I don't see anything like your syslog entries either in syslog or journal. Since one of the major differences between XUbuntu and Ubuntu is the use of Wayland as default display server on Ubuntu I'd try whether using X11 is more stable.

Holger

---

### Post by bingodingo on 2022-05-10
Thanks Holger, you may be right about x11 vs Wayland (no idea) but I'm still inclined if the instability continues too long to go back to Ubuntu 20.04 which has none of these problems. 22.04 just feels like a beta release at this point.

---

### Post by ajgreeny on 2022-05-10
Both of the browsers you mention are now provided by Ubuntu as snap packages, not as .deb packages.
This can make a huge difference to the way it is possible to use them with some restrictions on what they are able to open from local folders in your home.

Like Holger I use Xubuntu-22.04 not Ubuntu so can not use waylànd and do not have any experience of it, nor have I seen any real instability when using it, though I do note that it uses a lot more ram at idle than 20.04 did, approx 800MB instead of 550MB.
I have also removed all snaps from my systems and use either the .tar.gz direct from Mozilla for Firefox and one of the PPAs  for chromium. Both of these have been run ing successfully since I installed 22.04 when it was released.

---

### Post by GhX6GZMB on 2022-05-10
I have long been cured of "upgradeitis" and generally wait for at least the ".1" release (in this case 22.04.1) before even thinking about changing a working system.
Just my 5 cents.

---

### Post by guiverc on 2022-05-10
I agree with what's already been said; seeing a lot more bugs related to Wayland than users who use Xorg.

For me I find `chromium` & `firefox` as *snap* packages get closed rather regularly of late, as systemd-oomd decides they're using too much memory.  In systemd `journalctl` I'll see the following as example

```
May 09 20:55:58 d960-ubu2 systemd-oomd[889]: Killed /user.slice/user-1000.slice/user@1000.service/app.slice/snap.firefox.firefox.7d9b4142-0288-47c3-a5f6-ab77b8803604.scope due to memory pressure for /user.slice/user-1000.slice/user@1000.service being 62.09% > 50.00% for > 20s with reclaim activity
May 09 20:55:58 d960-ubu2 systemd[189875]: snap.firefox.firefox.7d9b4142-0288-47c3-a5f6-ab77b8803604.scope: Consumed 1h 8min 1.192s CPU time.
```

This is **not **likely your issue, but I'd check systemd's journal (`journalctl`)

---

### Post by bingodingo on 2022-05-10
Thanks everyone, useful messages here (avoid snaps, Wayland, releases < xx.04.01). 
The more I use 22.04 the more annoyances I find (even emacs is gimped).
To focus on my own work I think 20.04.04 is the way to go.
 I look forward to rejoining an improved 22.04 at a later date.

---

