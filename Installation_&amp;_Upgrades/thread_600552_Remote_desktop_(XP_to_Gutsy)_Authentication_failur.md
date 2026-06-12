---
title: "Remote desktop (XP to Gutsy) Authentication failure"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by rmills on 2007-11-02
In Fiesty, I was able to use VNC without any issues by enabling it in System > Preferences > Remote Desktop and setting a password.  Since upgrading to Gutsy, I have not been able to login via VNC.  I'm connected to my local network right now through my VPN.  From my XP work machine, I'm able to SSH into the Gutsy box fine.  I'm able to SSH and Remote (using TightVNC) into a second Fiesty box fine.  However, connecting via VNC from either the second Fiesty box or my work machine isn't working.  In both cases I'm getting a prompt for my password, which I'm entering, then getting an Authentication failure message.  In TightVNC all it says is "Authentication failure."  From the built in Terminal Server Client in the second Fiesty box, it says

VNC server supports protocol version 3.7 (viewer 3.3)
VNC authentication failed

Both systems are completely up to date.  It's clearly establishing a connection with the remote computer because I'm getting the password prompt, but it's not authenticating the session.  For sake of completeness, I've got Desktop effects enabled.

1) Why won't it authenticate?
2) Is there someway to fix this over SSH? (It'd be great if I could get to this today at work...I'm bored.)

---

### Post by grey_slime on 2007-11-30
I'm having the exact same problem, everything worked when I was on Feisty, I've upgraded to Gutsy and I am no longer able to authenticate.

Even stranger, when I set the connection to "Ask me before allowing a connection" and then try to connect I can establish the connection.

I have tried with TightVNC and RealVNC, same results.  Anyone have any ideas?

---

### Post by rmills on 2007-12-01
I found that when I don't ask for a password, it will connect.  Since most of the time I'm connecting remotely, I'm at work connecting through my encrypted VPN anyway I figured another layer of authentication wasn't necessary.  It doesn't solve the problem but it's a work around until I find a fix.

---

### Post by grey_slime on 2007-12-01
Yes, I guess that can work.  I am also running it only over SSH, so it should be alright.  It's a strange problem though.  Thanks anyways.

---

### Post by Milliways on 2007-12-03
> **rmills said:**
> In Fiesty, I was able to use VNC without any issues by enabling it in System > Preferences > Remote Desktop and setting a password.  Since upgrading to Gutsy, I have not been able to login via VNC.  I'm connected to my local network right now through my VPN.  From my XP work machine, I'm able to SSH into the Gutsy box fine.  I'm able to SSH and Remote (using TightVNC) into a second Fiesty box fine.  However, connecting via VNC from either the second Fiesty box or my work machine isn't working.  In both cases I'm getting a prompt for my password, which I'm entering, then getting an Authentication failure message.  In TightVNC all it says is "Authentication failure."  From the built in Terminal Server Client in the second Fiesty box, it says


I am having similar problems, except I get "Connection Refused 10061"
I am using VNC Viewer Free Edition on Windows.

It was working on Fiesty, and after upgrading to Gutsy (once I finally got that to work).

Suddenly it failed, after loading the batch of updates I had been ignoring.

I tried from a 2K machine (all on the same LAN) but can't get this to work either.

---

### Post by dvfreelancer on 2007-12-15
I'm having the same problem on Gutsy.  I'm trying to connect to another Gutsy machine.  They can see one another, password won't authenticate.  

Same symptoms.  It worked the first couple times, then some updates, now no workie.

Sat Dec 15 17:09:13 2007
 CConn:       connected to host crystal port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7

After entering password:

Sat Dec 15 17:09:19 2007
 main:        Authentication failure

And I already tried changing the password to something simple.  Just don't feel good about leaving it blank.  That's an accident waiting to happen.

---

### Post by dvfreelancer on 2007-12-15
I made a breakthrough and got it working.  It's a strange work-around and you have to do it exactly this way or it doesn't work. 

Go to System > Preferences > Remote Desktop

Uncheck the Require User To Enter This Password box.

Check the box again, enter the password and hit RETURN before closing the dialog box.  

If you skip the RETURN the authentication fails.  I'm sitting at one computer typing this response on the other one remotely.

I should add that I'm using one Ubuntu machine to log into another.  I'll go fire up the token Windows box and see if that works.

---

### Post by grey_slime on 2007-12-19
> **dvfreelancer said:**
> I made a breakthrough and got it working.  It's a strange work-around and you have to do it exactly this way or it doesn't work. 

Go to System > Preferences > Remote Desktop

Uncheck the Require User To Enter This Password box.

Check the box again, enter the password and hit RETURN before closing the dialog box.  

If you skip the RETURN the authentication fails.  I'm sitting at one computer typing this response on the other one remotely.

I should add that I'm using one Ubuntu machine to log into another.  I'll go fire up the token Windows box and see if that works.

Hmmm, I tried that and no luck for me.  It still fails even if i try to connect locally, like by typing vncviewer:localhost in the terminal (which by the way causes a nasty crash by recursively sharing desktops when it suceeds).  But I still get "Authentication Failure" whenever I try to connect.

I've given up on solving this and am relying on my firewall to restrict access and tunnelling the connection over SSH.

---

### Post by iampad on 2008-01-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This solution from [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032") solved my problem, I hope it might help.
> 
Binary package hint: gconf

Under fully updated 7.0.4 (as of 9/19/07), changing your remote desktop password is problematic.

What does NOT work is to open the Remote Desktop preferences, change the password, and close. Even logging off and then back on doesn't correctly change it (it seems to change it to something, but not to what I set it to.

To successfully change the password, I had to:
Open remote desktop preferences
Clear the password (delete all characters), close
logout and then back in
Open remote desktop preferences again
Set the password to what I wanted it to be
close, logout, then log back in


---

### Post by rmills on 2008-02-13
As a disclaimer, I didn't have an opportunity to try the last one.  However, the rest of the fixes didn't seem to work for me.  Thanks for the suggestions though.  I ended up backing up my home folder and reinstalling Ubuntu.  It was just that time of year anyway.  This issue doesn't seem to be present in a fresh install of Gutsy.  My suggestion: back up your home folders and reinstall.

---

### Post by rkillcrazy on 2008-02-25
> **rmills said:**
> As a disclaimer, I didn't have an opportunity to try the last one.  However, the rest of the fixes didn't seem to work for me.  Thanks for the suggestions though.  I ended up backing up my home folder and reinstalling Ubuntu.  It was just that time of year anyway.  This issue doesn't seem to be present in a fresh install of Gutsy.  My suggestion: back up your home folders and reinstall.

I tested it in a VM-Machine and it seemed to have done the trick.  Perhaps an update took place that broke things?  Hopefully there won't be an issue with 8.04.  The thing is, I'm currently at work and was trying to remote into my home PC.  I can SSH to it via PuTTY in WinXP but cannot VNC into it once I've made the connection.  Obviously, I can't go home and try what I did in the test above.  Is there a way to duplicate those steps through SSH?

02-25-08
1001 EST

---

### Post by Bobby Diaframm on 2008-03-24
> **rkillcrazy said:**
> I tested it in a VM-Machine and it seemed to have done the trick.  Perhaps an update took place that broke things?  Hopefully there won't be an issue with 8.04.  The thing is, I'm currently at work and was trying to remote into my home PC.  I can SSH to it via PuTTY in WinXP but cannot VNC into it once I've made the connection.  Obviously, I can't go home and try what I did in the test above.  Is there a way to duplicate those steps through SSH?

02-25-08
1001 EST

I think I had a similar issue to this. I'm running Ubuntu as a headless server. Had it all set up for remote desktop access, and it worked a treat. Something (i guess an update) turned off the automatic login, so I had to connect a keyboard and log in manually before I could get a VNC connection. Once logged in I connected via VNC and turned automatic log in on again. I too could connect with PuTTY, just not VNC.

---

### Post by ajonat on 2008-05-17
Ok. I figured this problem out.
The key thing is that the vnc password is not updated correctly.
The solution is to open gconf-editor and edit desktop > remote_access > vnc_password.
The vnc_password field is base64-encoded. Navigate to this page: [http://www.javazoom.net/services/base64/base64.jsp](http://www.javazoom.net/services/base64/base64.jsp), type your password and let the applet encode it. Paste the base64-encoded password in the vnc_password field and voila!
It works with and without SSH tunnel.
You don't have to logout/login, it just works!

Hope this help you.

P.S. I'm using feisty up-to-date.

---

