---
title: "Some sort of 12.04LTS (64) &quot;upgrade&quot; going on"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2014-07-12
I am not really sure what triggered it, but for the last 34 hours my 64-bit Ubuntu system has been "upgrading".  At first, it had to download almost 2.5GB of "files" and then while I was sleeping last night it started some sort of upgrade.  When I tried to check on what it was doing, the black area marked 'terminal' seemed to be doing something, but I have no idea what.

There were a lot of "can't find file", "having multiple values in 'test' may not work", and things like that.  There is a progress bar, and it seems to move glacially across the screen.  This "update" has been going on now for perhaps 14 hours (following the six hours it took to download 2.5GB of files).

When I went to click on my left-side taskbar, it blinked once, threw a "the system has detected an error" box in the middle of the screen and I cannot get rid of it by clicking either "send a report" or "Cancel".  It just keeps coming back.  AND, the taskbar has now disappeared, leaving me with just my wallpaper and this "updating" box running amok.

I have a sinking feeling that I am not going to be able to recover from this and will have to start all over agian with my distribution DVD of 12.04LTS.

Can anyone shed any light on just what this is and what it is trying to update?  I thought the "LTS" meant "Long Term Support".  Was I mistaken?

Bill

---

### Post by kostkon on 2014-07-12
Could you post some of the output or maybe a screenshot?

---

### Post by WB0HYQ on 2014-07-12
Well, that's problematic isn't it?  I cannot get ANYTHING to work on the computer.  Not terminal - nothing.  The output of the terminal area in the box marked "Running Partial Upgrade", rolls down so fast I'm not about to try and write it down longhand. :p

Similarly, I cannot get a screenshot unless I use my digital camera and then post what it sees.

The entire system is unresponsive to any mouse clicks or keyboard keystrokes.

Bill

---

### Post by WB0HYQ on 2014-07-12
More information (finally):

The "update" has managed to groan to an end.   The "Running Partial Update" box just disappeared and left me with nothing on the screen but wallpaper.

CTRL-Alt-F2 gave me a terminal which repeated the warning I saw two days ago:

QUOTE

Your current Hardware Enablement Stack (HWE) is going out of support on 08/07/14.  After this date security updates for critical parts (kernel and graphics stack) of your system will no longer be available.

For mor information, please see:

((gives a Wiki web page ))

To upgrade to a supported (or longer supported) configuration:

* upgrade from ubuntu 12.04 LTS to ubuntu 14.04 LTS by running:

sudo do-release-upgrade -p       (((<<<-- this is how I got started on this merry-go-round - I issued this command))))

OR

* install a newer HWE version by running"

(( huge, long command ))

and reboot your system.

END QUOTE

Since I'd already run the previous 'sudo' command, I simply rebooted the machine.

First off, I got a long string of "Failed to execute" stuff scrolling up the screen too rapidly to make a note of what failed.

Then, I got the 'normal' reddish-brown UBUNTU 14.04 LTS screen.  ((Used to be 12.04 LTS))

This eventually faded and after a bit I got a blank screen with two notices on it.  One said "Sorry.  A problem has been detected..." which disappeared almost immediately and left another one that said "apport-gtk  stopped".  This had a 'continue' on it, which I clicked.

Then the entire desktop I'm used to appeared and things seemed to be working.  I can start programs and they run, but some features of them don't work.  For instance, I use Variety to change wallpapers.  Before, I could use the mosue wheel on the small icon and it would change wallpaper.  This does not work.

[I][B]The real fly in the ointment is a notice that pops up every ten seconds and is VERY ANNOYING that tells me "Desktop Manager is not active".  I cannot get rid of it because it keeps popping back up.

How do I get that fixed?  ((at the moment, I drag it over to the side of the screen where it is out of the way.  But soon another appears that gets dragged away also.  I soon have a boneyard filled with notices saying the same thing.))[/B][/I]

I am terribly sorry for the long post, but this is the onoy way I can describe what's happening here.

Bill

---

### Post by WB0HYQ on 2014-07-12
Solved the 'Desktop manager' popup.  Uninstalled "pcmanfm" and it went away.

So, apparently, I am now (shakily) running UBUNTU 14.04 LTS.  There are some differences, but I think I can manage them.  The only thing I have to worry about now is upgrading my very old machine also running 12.04 LTS.  It has a very slow CPU and if my 3 core 64-bit machine takes 36 hours to update I shudder to think how long the old machine will take.

Bill

---

### Post by ajgreeny on 2014-07-12
I suspect that, maybe unbeknown to you, you have at some time in the past updated your original 12.04 and added a newer HWE for one of the ubuntu releases that has now lost it's support.  You could have updated the HWE alone, as far as I understand it, and not updated to 14.04, but I am not totally sure about this as I have not so far updated my 12.04 system by adding a newer HWE, though I have updated the kernel alone from the original to 3.5.0-52.
See
[http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support](http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support)
and
[http://askubuntu.com/questions/340874/lts-enablement-stacks-should-i-use-quantal-raring-or-saucy](http://askubuntu.com/questions/340874/lts-enablement-stacks-should-i-use-quantal-raring-or-saucy)
for some more details.

Are you sure you are now running 14.04?
Let's see the output of ```
lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -mrn
```which will tell us a lot about your system.

---

### Post by WB0HYQ on 2014-07-12
There was the message on the terminal that stated I could update to just a newer version of HWE (like you say), but when I entered the sudo command it barfed big time, failing almost every command in the update file.  That's when I entered the first sudo command (listed above in my long post).

I've been exercising my new installation of 14.04LTS and it seems to be stable now.  At least I'm not getting any failure notices.  I did have to completely reinstall my 'xscreensaver' because somehow it got uninstalled in the update.  Even that works now.

On my older computer running 12.04LTS I think I'll just wait and see what happens when support ends and go from there.  There's got to be a better way than wading through an 5-hour, 2.5GB download and then a 12-hour update session.

Thanks for the info though.

Bill

---

