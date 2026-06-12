---
title: "Ubuntu 10.10 won't finish installing"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by dmeisegeier on 2010-12-29
[FONT=Arial][SIZE=3]Hi,[/SIZE][/FONT]

[FONT=Arial][SIZE=3]I am trying to install Ubuntu 10.10 from a USB boot and think I got most of the way but it stopped at the “who are you? page. This is where I enter my name, computer’s name, user name and password. I entered that information but the “forward” button is not clickable at this point, only the “back” so I can't complete the install.[/SIZE][/FONT]

[FONT=Arial][SIZE=3]I saw 3 warnings and 1 error in the log at the bottom of the screen. I have provided the messages below. Note, where you see ??? it means it looks like there was more text but it went off my screen and I couldn't read it.[/SIZE][/FONT]

[FONT=Arial][SIZE=3](1) [/SIZE][/FONT]
[FONT=Arial][SIZE=3]Ubuntu clock-setup: rdate: adjust local clock by -0.020140 se???ds /usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1404: GtkWarning: IA_gtk_progr???_set_percentage: assertion ‘percentage >= 0 && percentage <= 1.0’ failed[/SIZE][/FONT]
[FONT=Arial][SIZE=3]self.install_progress.set+fraction(fraction)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]ubuntu ubuiqity[2720]: switched to page timezone[/SIZE][/FONT]

[FONT=Arial][SIZE=3](2)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Ubuntu kernel: [ 773.263101] EXT4-fs (sda1): mounted filessys ??? with ordered data mode. Opts: errors=remount-ro[/SIZE][/FONT]

[FONT=Arial][SIZE=3](3)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Ubuntu ubiquity: /usr/lib/python2.6/dist-packages/apt/depreca???n.py:96: UserWarning: Deprecated parameter ‘autoFix’[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3](4)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Ubuntu ubuiquity: warnings.warn(“Deprecated parameter %r” % ???) /usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1396: GtkWarning: IA__gtk_progr???_set_percentage: assertion ‘percentage >=0 && percentage <= 1.0’ failed [/SIZE][/FONT]
[FONT=Arial][SIZE=3]self.install_progress.set_fraction(fraction)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]ubuntu ubiquity[2720]: debconffilter_done: ubiquity.component???nstall (current: ubi-usersetup)[/SIZE][/FONT]
[FONT=Arial][SIZE=3]THAT WAS THE LAST LINE[/SIZE][/FONT]


[FONT=Arial][SIZE=3]Any suggestions?[/SIZE][/FONT]

[FONT=Arial][SIZE=3]Thanks![/SIZE][/FONT]

[FONT=Arial][SIZE=3]David[/SIZE][/FONT]

---

### Post by dmeisegeier on 2011-01-04
Well, I found the solution on another thread - I had used an upper case letter in my user name and apparently you can't do that. I switched to make them all lower case letters and voila - the "forward" button highlighted, I clicked it and the install went perfectly.

---

