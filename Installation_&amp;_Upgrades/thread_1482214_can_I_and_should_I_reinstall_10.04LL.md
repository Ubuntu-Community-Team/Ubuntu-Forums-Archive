---
title: "can I and should I reinstall 10.04LL ?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Chuck_N on 2010-05-13
Newbie with Linux OS. Upgraded from KK to LL (which I had thought might be called Leaping Lizards)  Took an hour or two to update KK first.  Then a couple hours installing LL. Various problems along the way and I was betting the install would be a failure. To my surprise it operates.
  However, I have various problems now: 1) the Firefox icon on the desktop has become a grey box (but FF runs),  2) YahooMail and Gmail and this Forum, now require signin every day, even though when I got a warning message related to cookies, I confirmed the settings and even, for the first time, checked the box to accept 3rd party cookies,  3) I get large grey boxes on the output screen when paging through a long document, 4) and various other difficulties including blowing-up at some random times, with dozens of lines of system messages.
   I guess my main question is: can I and should I try to REinstall 10.04LL?
If so, how do I go about doing it?
  Thanks, Chuck_N

---

### Post by dino99 on 2010-05-13
thats a summary of bad things we can have with the dist-upgrades: old and broken symlinks/settings left behind and pushiing some issues: most of them are with the hidden files (.mozilla, ...), if you have previously export your data, bookmarks and passwords, then simply delete these hidden files, on next reboot they are recreated.

or/and you can clean the system: be sur that your sources.list only have genuine lucid repo, then clean, autoclean, autoremove, update and install -f.

you can install gconf-cleaner and bleachbit to remove to old noisy things and reconfigure the broken apps:

sudo dpkg-reconfigure "the app"

---

### Post by Chuck_N on 2010-05-14
> **dino99 said:**
> thats a summary of bad things we can have with the dist-upgrades: old and broken symlinks/settings left behind and pushiing some issues: most of them are with the hidden files (.mozilla, ...), [COLOR=Red]if you have previously exported your data, bookmarks and passwords, then simply delete these hidden files, on next reboot they are recreated.[/COLOR]

[COLOR=Red]or/and you can clean the system: be sure that your sources.list only have genuine lucid repo, then clean, autoclean, autoremove, update and install -f.[/COLOR]

[COLOR=Red]you can install gconf-cleaner and bleachbit to remove to old noisy things and reconfigure the broken apps:[/COLOR]
[COLOR=Red]
sudo dpkg-reconfigure "the app"[/COLOR]

the stuff in red I can't quite understand.
remember, I'm a newbie.
I don't think I have previously exported my data and passwords.

---

### Post by Chuck_N on 2010-05-28
okay, I built a liveCD and used it to REinstall Ubuntu 10.04 LL

Seems to be running fine.

I just got into Command Line and wanted to quit.
Spent an hour; read Ubuntu Pocket guide. 

Read thru the online list of commands.  Tried various words, like
Cancel  Done  Exit  Halt  Return  Stop   and others

Tried all the F-Keys and various ctrl- and alt- combinations.

Finally powered down.

So, how does a person get out of the command line?

---

### Post by darkod on 2010-05-28
I know

sudo reboot

will restart the machine. I guess

sudo shutdown

might power it down. :)

---

### Post by Chuck_N on 2010-05-28
> **darkod said:**
> I know

sudo reboot

will restart the machine. I guess

sudo shutdown

might power it down. :)


thanks so much.

now, if I can just remember that next time.....

or remember where I wrote it down   8-)

ah, I'll write it in my Ubuntu Pocket Guide
in the chapter on Command Line.

---

### Post by WinRiddance on 2010-05-28
Try **sudo apt-get install gpass** and use that nifty little utility for all of your passwords as opposed to keeping them stored in your FF settings. Principle is the same, one master password to unlock the application. Difference is that if you ever do another clean Ubuntu installation just keep a copy of your Gpass folder (located in home/user) and you'll never lose your passwords again.

What happened with your installation is that you received a new installation of the latest and greatest FF. But since you didn't have your settings exported these were lost and consequently not included with the new installation of FF.

You can backup/export all of your FF bookmarks and save them regularily (every month or so) too. If you have Thunderbird for email you can export and save those settings as well. I keep all of my personal files on a separate partition. That way I never have to worry abot a new installation, reinstallation, whatever. My important personal stuff is always safe that way. Keeping your current stuff backed up is really so important. Enjoy your Ubuntu ....

---

### Post by Chuck_N on 2010-05-29
if I use ctrl-alt-F2 to get to command line, is there no way to get straight back to Ubuntu?
I have used    sudo reboot    okay, but is it necessary? I have an Ubunto Pocket-Guide and have done online-searching, but can't seem to find much.


More importantly, when I enter command-line mode, I get:
  [COLOR=Magenta] Your CPU appears to be lacking expected security protections.  Please check BIOS settings[/COLOR]

then I get

 [COLOR=Magenta]   This CPU is family 15 model 4, and has NX capabilities but unable to use these because BIOS is configured to disable the capability.  Please enable in BIOS.  [/COLOR]

then I am told to see   [COLOR=Magenta] [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)[/COLOR]

if I enter that I get  [COLOR=Magenta] No such file or directory.[/COLOR]    NOTE: I just answered part of my troubles here. I see that  https  above is a link for a web location, not to be entered in command-line.  Duh.  I'll go to that page and
   do some reading.

I am using a Compaq Presario  SR1503WM with two 40-gig drives. The main boot-drive is Ubuntu 10.04 LL, recently built from liveCD.  The second drive is windows2K , alternate boot drive,  no longer functioning.

---

### Post by praveen_pa on 2010-08-06
try startx command in the console

---

### Post by Chuck_N on 2010-08-06
> **praveen_pa said:**
> try startx command in the console

I did.  I get     User not authorized to run the X server, aborting.

---

### Post by rtimai on 2010-08-26
Chuck, I can't believe nobody told you that the Desktop should be in Ctrl-Alt-F7 (tty7.) That's if you "got to the control line" using Ctrl-Alt-F1-F6. Yes, there are 6 terminals, besides the windowed Terminal.

I should note here that occasionally I find the desktop on tty8 (Ctrl-Alt-F8) instead of tty7, and tty7 is a blank screen, with no login prompt, an unresponsive blinking cursor, e.g. nothing appears on the screen that I enter on the keyboard. Don't know why that happens. Restarting restores the desktop to the default tty7.

Arggh. I don't know why I can't type F-eight here, it keeps appearing as a smiley.

---

### Post by Chuck_N on 2010-08-27
ah, yes,  ctrl-alt- F6  gets me there 
and   ctrl-alt- F7   gets me back.

is it best to exit from control-line before returning?

thanks.

---

### Post by rtimai on 2010-08-27
Myself, yes, I do always log off with 'exit' before returning to the desktop (Ctrl-Alt-F7,) unless I plan to later go back to the command line. But I'm being conservative -- I don't know definitely if it's necessary.

---

