---
title: "root pasword changed"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by tommyatkins on 2012-09-10
I just upgraded from 10.04 to 12.04. everything worked fine except my root password was changed!!!!
I can log in to other users but not my administrator account.

I am stuck big time.

Any help would be appreciated.

Tommy Atkins:(

---

### Post by tommyatkins on 2012-09-10
Any help???

I can not do anything

Tommy Atkins

---

### Post by Rex Bouwense on 2012-09-10
Have you tried looking here

[https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html)

---

### Post by tommyatkins on 2012-09-10
My administrator password is the one that has been trashed. When I try running sudo in a window it will not take neither the adm's  paswd nor the account paswd under which I am running the terminal.

---

### Post by Cheesemill on 2012-09-10
You can reset your password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tommyatkins on 2012-09-11
I have tried this suggestion. even though I am in the root mode it will not change the pass word

---

### Post by tommyatkins on 2012-09-11
I am not sure if this is the right forum for this question. I am having trouble with my Administration pwd so I downloaded the 12.04 version of the restore utility CD as it seemed to be the be best thing to try. I have looked at their documentation file but I can not figure out how to use it to change the Adm password. If some one could just point me in the right direction I would be grateful

Tommy Atkins.

---

### Post by darkod on 2012-09-11
What password are you actually talking about? Your user password?

In ubuntu, you use the password of the user that was created as first to run the sudo command which does admin tasks. There is no separate admin password in the real meaning of that.

To change a user password, you can boot the recovery mode of ubuntu (it's in the grub2 boot menu), and do it there:
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

It is listed under The Standard Way procedure.

---

### Post by coffeecat on 2012-09-11
@tommyatkins, I have merged your two threads - they are about the same issue.

Perhaps you could clarify what you mean by the "12.04 version of the restore utility CD".

I suggest you have another look at the various links posted. They describe essentially the same method for resetting your password, and they are unlikely to fail if run correctly.

---

### Post by tommyatkins on 2012-09-11
What happened was I updated from 10.04 to 12.04. The pass words for all my users _EXCEPT_ the administrator's remained the same. I, your humble Sys Adim, can not log into my own account. When I did the update I was not asked for a pass word for any of the accounts. The only way I can use the internet is to log into my Wife's account. When I  goggled into Ubuntu  the best fit seemed to me to be their recovery disk for 12.04 which I have dowm loaded but need help in using.

---

### Post by coffeecat on 2012-09-11
> **tommyatkins said:**
> When I  goggled into Ubuntu  the best fit seemed to me to be their recovery disk for 12.04

What exactly do you mean by this? If you mean the [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"), that looks to be unsuitable for what you want. Or do you mean the live desktop CD from the ubuntu.com site? It is possible to reset your password by chrooting into your installation from the live CD, but since you'd be running the same command as you say you've already tried from the recovery console, there would be no point.

All you should need to do is to boot up in recovery mode. Choose "drop to root shell" and you will be confronted with a text console with a # prompt. Run this command:

```
mount -o rw,remount /
```

Now this:

```
passwd *yourusername*
```

Obviously, substitute your log in account name for *yourusername*. You will be prompted for the new password twice - even though you are probably trying to reset your old password, treat it as though you were entering a new password. Do you get an error message? If not run this command:

```
reboot
```

And see if you can log in now.

---

### Post by tommyatkins on 2012-09-12
I finally able to get into recovery mode. i could not do the mount -o rw, remount / as the remount command does not exist. I went and did ls/hone. I did passwd tommy1 entered the old passwd twice and it said that the pass word was changer. I rebooted and I still could not  log in to my administrator account. I did the same thing for another regular user and everything took!!!! If anyone has some other ideas I would be gladdto try them.

---

### Post by darkod on 2012-09-12
I think you should really stop saying administrator account. If your user is tommy1, just say that. Opposite from windows, in ubuntu DOES NOT exist user called Administrator. So you are just confusing things when saying that.

Yes, the first user has the power to run sudo commands, but don't call it administrator, it's still your user (or someones).

You need to mount the root partition as read/write, so if that command didn't work for you (it should), try this:
After selecting the recovery mode, at the menu that shows first select network. That will enable networking but at the same time mount the root partition as r/w.
Then select root (drop to root shell) from the same menu, and do the password change.

After that reboot, you can literary use the command reboot and it will restart. Boot the normal mode, and see if you can log in tommy1 with the newly selected password. Tell us if that worked.

After that, if tommy1 can't run sudo commands and he should be able to, maybe the sudoers file got corrupted, and deleted the sudo rights of tommy1.
But you should at least be able to log in with the changed password, lets see if that worked first.

---

### Post by coffeecat on 2012-09-12
> **tommyatkins said:**
> I finally able to get into recovery mode. i could not do the mount -o rw, remount / as the remount command does not exist.

@tommyatkins, the command is not as you have posted:

```
mount -o rw, remount /
```

But this:

```
mount -o rw,remount /
```

No space between the comma and remount.

I'm not being unkind, but I have to say this. You are making many typos in your posts, and you mistyped the command I posted. Please slow down and be absolutely sure that you are not setting a mistyped password, or trying to log in with a mistyped password. This is the commonest cause of a failed password. Without the visual feedback of the actual characters you are typing in, it is easy to make a mistake. Experienced users do so. The commands you have been given really should work, if you are typing them and the new password in correctly.

---

### Post by tommyatkins on 2012-09-12
I tried your suggestion I selected the network option. that did make root as read write. I selected root then did ls /home. tommy1 was there and I did the passwd tommy1 changed the pass word . The system said it was updated. I still could not log in to Thomas Atkins,. I did this twice with the same results. There was a new post that said there should be no space between rw, and remount.. I will give that a try.
Thanks for your help

---

### Post by tommyatkins on 2012-09-12
I tried mount command with no space between rw, and remount. That worked fine. I then did the passwd  tommy1 sequence, rebooted  and I still can not log in to the tommy1 account.

---

### Post by darkod on 2012-09-12
That IS weird. It should at least allow you to login even if you can't do sudo with it.

It might sound like a stupid question, but are you sure that's the correct user? Because tommy1 is the username and in the login screen it prints the full first and last name. Are you selecting the correct user first and last name that correspond to tommy1?

Try this, at the login page, press Ctrl + Alt + F1 (I think), that should open a terminal window asking for login in text mode. Use the tommy1 username and the password you changed. Does it log you in?

---

### Post by tommyatkins on 2012-09-12
THAT WORKED!!!!! This log in page, under the GUI looks the same as the one I used in version 10.04 but I guess it just got corrupted in the update process. The two previous updates I did a clean install and had no problems. I thought just upgrading should be easier. What a big mistake that was. After I log in via the terminal how do I get back to the GUI?
Thanks again for all your help.

---

### Post by darkod on 2012-09-12
Unfortunately I don't have an answer to that. It goes beyond my ubuntu knowledge.

Usually you would try with startx, but when I tried that it said there is open GUI session in terminal #7 (Ctrl + Alt + F7), which is the login page waiting for your login.

So, I'm not sure you can fire up the GUI after you have logged in in text mode in terminal #1.

Were there any error messages or warnings when doing the upgrade? Is it possible all packages didn't finish the upgrade?

To finish pending packages, or fix broken ones, you can do again the recovery mode, network, drop to root shell and try:
```
dpkg --configure -a
apt-get install -f
```

You might be able to run that logged in in terminal #1 too, in text mode. You will just need to add sudo in front of the commands because you are not in the root shell.

I'm running out of ideas if that doesn't help.

---

### Post by tommyatkins on 2012-09-12
I will see what I can workout tomorrow. 
It is almost time for dinner.
Thanks again for all your help.

---

### Post by opensshd on 2012-09-13
Saw something here that sounded a lot like what you're describing:
 
[http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04](http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04)

Is there anything helpful in logfiles?

/var/log/syslog
/var/log/Xorg.0.log
/var/log/auth.log

---

### Post by tommyatkins on 2012-09-13
This reference points to dual monitors which I do not have. I am marking this thread as fixed and gather some more information for a new thread.

---

### Post by opensshd on 2012-09-13
just yesterday someone had an issue with a keyboard that was solved (at least till they could update BIOS) by removing and reinserting the laptop battery... go figure ;)

Sometimes the answers are a bit 'unconnected looking' :P

I'd definitely take a look at your auth.log though, that may well have some pertinent info.

---

