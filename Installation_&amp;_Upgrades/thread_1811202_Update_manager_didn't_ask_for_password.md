---
title: "Update manager didn't ask for password"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2011-07-24
I just checked for updates using update manager. It found some (49) updates recommended/required, but when I clicked 'update', it started and completed the update w/o asking for sudo password.

That's not good, is it?

---

### Post by elliotbeken on 2011-07-24
When did you last enter your password as if it was recent it will not ask again ?

---

### Post by aeronutt on 2011-07-24
> **elliotbeken said:**
> When did you last enter your password as if it was recent it will not ask again ?

I thought about that, and the first time I actually killed the download of the files, logged out, logged back in, check for updates...and it still installed w/o a password.

---

### Post by aeronutt on 2011-07-29
It just did it again. I'm 100% confident I had not typed in my sudo password since I booted.

---

### Post by Old_Grey_Wolf on 2011-07-29
Hum, that is strange. I have never seen updates that are labeled as "required". If you installed the updates as you said you did; then, it shouldn't be giving the option to install them again.

Do you get any further error messages when you enter "sudo apt-get update" and "sudo apt-get upgrade"?

Are you using commands; such as, "sudo -i" before this happens?

---

### Post by aeronutt on 2011-09-27
Any new thoughts on this folks? I've absolutely confirmed that when I:
- Boot the computer
- Log in
- Run the 'update manager' GUI
- click on 'check'
- click on 'install updates'

that I'm *never* asked for sudo password.

I've also confirmed that if I run apt-get, I must run with sudo prefix.

---

### Post by aeronutt on 2011-10-01
Anyone? I'd really like to confirm if this is normal or if this is a security risk.

If you're using 11.04/Natty, are you requested to enter the sudo password when using the update manager GUI?

---

### Post by hakermania on 2011-10-01
> **aeronutt said:**
> Anyone? I'd really like to confirm if this is normal or if this is a security risk.

If you're using 11.04/Natty, are you requested to enter the sudo password when using the update manager GUI?

Just checked, all nomral here, 'Check for Updates' requires no passwd but 'install updates' does. ):P

---

### Post by aeronutt on 2011-10-01
> **hakermania said:**
> Just checked, all nomral here, 'Check for Updates' requires no passwd but 'install updates' does. ):P

Thanks for checking!

Well..something's odd on mine then. 'install updates' does NOT request a password for me. Oddly, I did a fresh install of 11.04 on another partition, and it does NOT require a password for 'install updates' either!!!

---

### Post by Kisbey on 2011-10-19
Interesting, this just occurred for me as well, 11.10 Oneiric.  Logged in this morning to check news and whatnot, system notified me there were some updates.  I clicked update but was never asked for a password.  I was so surpised I Googled "Ubuntu didn't ask for password" and landed here.

---

### Post by aeronutt on 2011-10-19
Yea, oddly, I definately remember my 11.10 install requesting a password the first few times, but .... not anymore. No password required to do updates now on 11.10.

---

### Post by aeronutt on 2011-10-25
Now, update-manager is asking for password again in my Oneiric install.  Anyone have a definitive answer as to if update-manager should or shouldn't always be asking for a password?

---

### Post by houseworkshy on 2011-10-25
I'm still on the lts so this may be something new.  However I suspect that it should ask for a password.  You could try opening a terminal and entering "sudo -k" that should kill sudo privalages.  Then close the terminal and try the update thing again.  If you are not asked for a password then it would ring alarm bells for me.  Remember though that sudo has a default timer of 15 minets.  Actually "sudo -k" is a pretty good idea after sudo anything, especially if one is browsing.

---

### Post by aeronutt on 2011-10-27
> **houseworkshy said:**
> I'm still on the lts so this may be something new.  However I suspect that it should ask for a password.  You could try opening a terminal and entering "sudo -k" that should kill sudo privalages.  Then close the terminal and try the update thing again.  If you are not asked for a password then it would ring alarm bells for me.  Remember though that sudo has a default timer of 15 minets.  Actually "sudo -k" is a pretty good idea after sudo anything, especially if one is browsing.

Good idea, but nope. Sudo -k made no difference. Password not required to update via update-manager.

---

### Post by rojaasensei on 2011-10-27
I just noticed the same phenomena today.
Strange

---

### Post by foresthill on 2011-10-27
Wow, this does not inspire a great deal of confidence in the security of that version of the OS. How could something as critical as that get overlooked? Kind of makes you wonder what other important stuff got neglected that has not yet come to light.

The more I see going wrong with the newer versions, the more I'm inclined to hold off on upgrading. I'm still waiting for bugs in 11.04 to get ironed out before I migrate to that version.

Sticking with 10.10 for now (maybe forever).

---

### Post by scania_gti on 2011-10-27
Maybe in update manager settings cheked "install automaticaly"?

---

### Post by aeronutt on 2011-10-27
> **foresthill said:**
> Wow, this does not inspire a great deal of confidence in the security of that version of the OS. How could something as critical as that get overlooked? Kind of makes you wonder what other important stuff got neglected that has not yet come to light.

The more I see going wrong with the newer versions, the more I'm inclined to hold off on upgrading. I'm still waiting for bugs in 11.04 to get ironed out before I migrate to that version.

Sticking with 10.10 for now (maybe forever).

FYI, for me, this characteristic has been noticed in 11.04 and 11.10.

---

### Post by DrJohn999 on 2011-10-27
Same here -- but only since upgrading to 11.10 -- no password prompt for Update Manager to either check for updates or install, while synaptic, aptitude and apt-get prompt as expected. In my case I have multiple unresolved dependencies probably as a result of the upgrade to 11.10 over some ppa type repositories, but perhaps this is a different problem. My thought is to simply wipe the system partitions and reinstall from a checksum-verified image.

---

### Post by foresthill on 2011-10-30
Turns out it's not a bug, it's a FEATURE. :lolflag:

---

### Post by Script Warlock on 2011-10-30
from [security]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates") team

Update Manager doesn't prompt for security updates

Why does update-manager no longer prompt for the user's password?

As of Ubuntu 11.10, update-manager no longer prompts for the user's password to apply updates. This was decided to improve usability and to make it easier for users to apply security updates and therefore increase system security. The rationale is as follows:

Like in previous releases, by default only people in the admin group are allowed access to perform security updates.

Only updates for already installed software can be applied without a password. Installing additional software still requires people to enter their password.
The password prompt had become an irritant for some people such that they would just press 'Cancel' instead of installing the updates. The password prompt decreased system security for those users.
People that did dutifully apply updates became conditioned to enter their privileged password perhaps daily. When the user is prompted for the password, it should mean something and the frequency of update-manager updates meant that some people no longer thought about why they were entering their password. For these users, the password prompt had the potential to reduce security.

For environments where this change is deemed not appropriate, this functionality can be disabled by the administrator via PolicyKit or by creating users that are not in the admin group (a recommended practice to begin with).

---

### Post by foresthill on 2011-10-30
Hmm. So it is indeed a "feature".

Sort of reminds me of how Ubuntu a couple versions back stopped asking for a password to mount other partitions on the hard drive, which I did not like because it allowed someone I allowed to use my computer browse my Windows partitions and files. 

I like security and passwords myself, that's one of the main reasons why I use Linux. And I don't like the trend toward idiot-proofing the OS, but there's not much I can do to stop it. :(

---

### Post by aeronutt on 2011-10-30
Thanks, at least now I know nothing's wrong with my system.
But, sounds like it's dummying down security. I'm guessing figuring out how to disable this 'feature' isn't trivial for the average user. Any tutorial on 'policykit' relative to disabling this?

---

### Post by philinux on 2011-10-30
> **aeronutt said:**
> Thanks, at least now I know nothing's wrong with my system.
But, sounds like it's dummying down security. I'm guessing figuring out how to disable this 'feature' isn't trivial for the average user. Any tutorial on 'policykit' relative to disabling this?

I really see this as an improvement as it only exhibits this behavior for installed software and the admin user. There is no security risk in this.

---

### Post by unknown user on 2012-05-14
I also came across this issue the other week and thought that my system was playing up. it is good to hear that it is a feature and not a bug. I am still in two minds though if I think it is a good feature or not. Possibly the better way around it would be to allow users the option to either enable or disable it via a check box un the update manager preferences screen. That way you cover both angles and keep everyone happy.

---

### Post by jazzerit on 2012-05-22
> **philinux said:**
> I really see this as an improvement as it only exhibits this behavior for installed software and the admin user. There is no security risk in this.

I dunno... I mean, if someone malicious gets control of the repositories, couldn't they push out malicious updates? It's pretty unlikely, but I assume it could happen.

---

### Post by zombifier25 on 2012-05-22
> **jazzerit said:**
> I dunno... I mean, if someone malicious gets control of the repositories, couldn't they push out malicious updates? It's pretty unlikely, but I assume it could happen.

No, at least very very very hard. Even if some hackers took control of the repository, they still cannot digitally sign the packages. If Ubuntu detects unsigned packages while updating, it will scream out something like "untrusted packages" or sort.

---

### Post by jazzerit on 2012-05-22
> **zombifier25 said:**
> No, at least very very very hard. Even if some hackers took control of the repository, they still cannot digitally sign the packages. If Ubuntu detects unsigned packages while updating, it will scream out something like "untrusted packages" or sort.

Oh yeah... I forgot about that. I sort of knew that ubuntu signs it packages, I'm just being very tired, and thinking about what happened over at kernel.org a little while ago. But yeah, Thanks for that.

---

