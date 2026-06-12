---
title: "update for &quot;Shell Shock&quot; / or how to remove bash"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2014-09-25
Hi, is there an update for the 'shell shock' bug yet, or advice on how to remove bash or otherwise deal with this?
when I try to sudo apt-get update, I get an error 'Could not resolve 'dl.google.com' - any advice?
Could not resolve 'dl.google.com'



Thanks

---

### Post by Newbunto on 2014-09-25
Is there any specific information about this vulnerability, never mind about how to deal with it?

What is the vulnerability? Who is vulnerable and who is not? What is the attack mechanism?

---

### Post by Newbunto on 2014-09-25
Some info:

[https://blog.cloudsecurityalliance.org/2014/09/24/worse-than-heartbleed/](https://blog.cloudsecurityalliance.org/2014/09/24/worse-than-heartbleed/)

[https://access.redhat.com/articles/1200223](https://access.redhat.com/articles/1200223)

I've already seen Robert Graham's mass scan visit one of my web servers checking for this vulnerability.

---

### Post by chris294 on 2014-09-25
[https://community.qualys.com/blogs/securitylabs/2014/09/24/bash-remote-code-execution-vulnerability-cve-2014-6271](https://community.qualys.com/blogs/securitylabs/2014/09/24/bash-remote-code-execution-vulnerability-cve-2014-6271)

doesn't matter too much - easy to fix and test.

[COLOR=#333333][FONT=Open Sans]A simple test to check if your Bash is vulnerable is available publicly.[/FONT][/COLOR][COLOR=#333333][FONT=Anonymous Pro][FONT=inherit]
[/FONT]

[LIST=|INDENT=1]
[*][COLOR=black][FONT=inherit !important][FONT=inherit !important]$ env var='() { ignore this;}; echo vulnerable' bash -c /bin/true[/FONT][/FONT][/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]Upon running the above command, an affected version of bash will output "vulnerable".[/FONT][/COLOR]

[COLOR=#333333][FONT=Open Sans]Once the patch has been applied, the same test will return the following result.[/FONT][/COLOR][COLOR=#333333][FONT=Anonymous Pro][FONT=inherit]
[/FONT]

[LIST=|INDENT=1]
[*][COLOR=black][FONT=inherit !important][FONT=inherit !important]bash: warning: var: ignoring function definition attempt  [/FONT][/FONT][/COLOR]
[*][COLOR=black][FONT=inherit !important]bash: error importing function definition for 'var'  [/FONT][/COLOR]
[/LIST]
[/FONT][/COLOR]

if vulnerable then .. 
apt-get update
apt-get install bash
then re-run the above test
then go have a milkshake

---

### Post by moda2 on 2014-09-25
test if your bash is vulnerable

# env x='() { :;}; echo vulnerable' bash -c 'echo this is a test'

---

### Post by deadflowr on 2014-09-25
> **Hodor said:**
> Hi, is there an update for the 'shell shock' bug yet, or advice on how to remove bash or otherwise deal with this?
when I try to sudo apt-get update, I get an error 'Could not resolve 'dl.google.com' - any advice?
Could not resolve 'dl.google.com'

Seems that's a google repo.
Do you have google packages installed?
You might temporarily try disabling those repos so the update manager can get the ubuntu packages updated.
After that try re-enabling them after the ubuntu packages are updated.

And bash is an essential package, so don't try removing it.




> **Newbunto said:**
> Is there any specific information about this vulnerability, never mind about how to deal with it?

What is the vulnerability? Who is vulnerable and who is not? What is the attack mechanism?

Ubuntu Security Notices[URL="http://www.ubuntu.com/usn/"]
http://www.ubuntu.com/usn/[/URL]

The Bash security notice
[http://www.ubuntu.com/usn/usn-2362-1/](http://www.ubuntu.com/usn/usn-2362-1/)

---

### Post by Lars Noodén on 2014-09-25
> **deadflowr said:**
> The Bash security notice
[http://www.ubuntu.com/usn/usn-2362-1/](http://www.ubuntu.com/usn/usn-2362-1/)

These notices are also sent out via the security mailing list, if you (@hodor) want to follow:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)
They include only a little explanation but do provide pointers to more.

Otherwise, checking for and applying updates daily works.  

I wonder if this bug will be marketed as a brand name like another recent one that does not need to be mentioned.

---

### Post by Hodor on 2014-09-25
Thanks everyone for the help - all sorted.

---

### Post by oldrocker99 on 2014-09-25
oops

---

### Post by deadflowr on 2014-09-25
> **Lars Noodén said:**
> These notices are also sent out via the security mailing list, if you (@hodor) want to follow:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)
They include only a little explanation but do provide pointers to more.

Otherwise, checking for and applying updates daily works.  

I wonder if this bug will be marketed as a brand name like another recent one that does not need to be mentioned.

+1 to subscribing to the mailing list, you can eiher get an email per announcement(bug alert) or a daily digest.
+2 to setting security updates to daily.

ShellShock is the Branded Name, so far.

---

### Post by Newbunto on 2014-09-25
On my Ubuntu laptop this update came through automatically, so that when I tested it for this vulnerability at the start of this thread it was already not vulnerable.

On my Ubuntu VPSs, I had to install the update manually (as per chris294's post above).

So I think Ubuntu has this covered.

Now on to some other computers that are running other distros ...

Edit: All my Ubuntus are LTS versions. If you are not running an LTS version, YMMV.

---

### Post by oygle on 2014-09-26
I'm running 13.10 , and can't see any updates for that release at [http://www.ubuntu.com/usn/usn-2362-1/](http://www.ubuntu.com/usn/usn-2362-1/)

Also, I haven't had updates for a while. Checked in Muon history and it was Aug sometime the last one ?? I have done ..

sudo apt-get update

but nothing appears for updates. Also, there are no .DEB files in the /var/cache/apt/archives . That's where they used to be. I use BASH a bit, and am behind a NAT firewall. 

Can someone please advise how to get the updates again ?

---

### Post by QIII on 2014-09-26
13.10 is EOL and is no longer receiving updates.

You need to do a fresh installation of 14.04 immediately.

---

### Post by oygle on 2014-09-26
Oh, okay thanks for that. I see that it says I'm "vulnerable", however I'm the only user on this computer and I'm behind a firewall.

Will start the backups today. Thanks

---

### Post by AgentZ86 on 2014-09-26
[http://arstechnica.com/security/2014/09/bug-in-bash-shell-creates-big-security-hole-on-anything-with-nix-in-it/]("http://arstechnica.com/security/2014/09/bug-in-bash-shell-creates-big-security-hole-on-anything-with-nix-in-it/")

Should I don't understand this test and it the test itself save to run ? 

What do you think of the info on this page ? 
Have I been patched already ? 

Please advise

---

### Post by mörgæs on 2014-09-26
Threads merged.

---

### Post by rickfoosusa on 2014-09-26
According to internet storm center there is a second variation of the vulnerability.
[https://isc.sans.edu/forums/diary/Update+on+CVE-2014-6271+Vulnerability+in+bash+shellshock+/18707](https://isc.sans.edu/forums/diary/Update+on+CVE-2014-6271+Vulnerability+in+bash+shellshock+/18707)

# On a patched system this will leave an empty echo file.
# env 'X=() { (a)=>\' sh -c 'echo date'

---

### Post by deadflowr on 2014-09-26
> **rickfoosusa said:**
> According to internet storm center there is a second variation of the vulnerability.
[https://isc.sans.edu/forums/diary/Update+on+CVE-2014-6271+Vulnerability+in+bash+shellshock+/18707](https://isc.sans.edu/forums/diary/Update+on+CVE-2014-6271+Vulnerability+in+bash+shellshock+/18707)

# On a patched system this will leave an empty echo file.
# env 'X=() { (a)=>\' sh -c 'echo date'

The original patch was determined to be incomplete, so a second patch was release 
see
[http://www.ubuntu.com/usn/usn-2363-1/](http://www.ubuntu.com/usn/usn-2363-1/)
and
[https://bugs.launchpad.net/ubuntu/%2Bsource/bash/%2Bbug/1373781](https://bugs.launchpad.net/ubuntu/%2Bsource/bash/%2Bbug/1373781)

So, don't be surprised if you see more patches...

---

### Post by JKyleOKC on 2014-09-26
> **oygle said:**
> Oh, okay thanks for that. I see that it says I'm "vulnerable", however I'm the only user on this computer and I'm behind a firewall.That, unfortunately, won't protect you. It's a quite subtle bug but it can allow the baddies to do anything they want with your machine. In itself it's just a skeleton key that unlocks total access, but once they get in the sky is their only limit.

If you can't upgrade to a current version that's getting security updates, then your options are pretty few in number and all are rather poor: replace "bash" with another shell that doesn't have the problem (and when you do, expect half or more of your programs to totally stop working), switch over to FreeBSD or OpenBSD instead of any version of *buntu (which will be more painful than upgrading to the current *buntu versions), or disconnect entirely from the net!

---

### Post by linux-klomp on 2014-09-26
I'm still on Saucy.
It says I'm up-to-date, but still vulnerable...
Is there an update for it or do I need to upgrade to Trusty?

---

### Post by deadflowr on 2014-09-26
> **linux-klomp said:**
> I'm still on Saucy.
It says I'm up-to-date, but still vulnerable...
Is there an update for it or do I need to upgrade to Trusty?

Yes upgrade.
Saucy is unsupported and will never get the patches for bash, or any other vulnerable application.

---

### Post by Ebelie on 2014-09-27
What if I just remove bash with apt-get remove bash? And then create a symlink /bin/bash -> /bin/dash? Problem solved? :-k

---

### Post by JKyleOKC on 2014-09-27
Will dash still execute the ~/.bashrc file each time it starts? If not, you may find a drastically different and apparently broken system after such a simplistic change. At the very least, you may need to modify ~/.profile to handle things differently, not to mention the shebang lines for many executable scripts...

---

### Post by bobipod on 2014-09-27
env x='() { :;}; echo vulnerable' bash -c 'echo this is a test'

i've run the above command but i get no comment it just sets up another ready command line.

am i missing something (apart from a greater knowledge of how linux works)

---

### Post by JKyleOKC on 2014-09-27
This:> bash -c[COLOR="#FF0000"] '[/COLOR]echo this is a test'should be:> bash -c echo[COLOR="#FF0000"] '[/COLOR]this is a test'It's an easy mistake to make!

---

### Post by SookieLaLaLaFoe on 2014-09-27
Unfortunately the 14.04 security update is still not sufficient. 

check: 
env X="() { :;} ; echo busted" `which bash` -c "echo completed"

busted
completed

To fix: 
sudo apt-get install -y bash

Fixed just fine now.

---

### Post by QIII on 2014-09-27
It has certainly already been updated on mine by doing normal updates.

```
xxxxxxx@Zack:~$ env X="() { :;} ; echo busted" `which bash` -c "echo completed"
completed
```

When was the last time you updated?

---

### Post by SookieLaLaLaFoe on 2014-09-27
Directly before posting. Doesn't make sense, but there you go. Not sure what's going on. A little unnerving really. This is using the stock GUI software updater, letting it update its sources, etc, restarting. Second variant still worked until I swapped out bash manually.

---

### Post by QIII on 2014-09-27
Did you do 

```
sudo apt-get update
```

and then

```
sudo apt-get upgrade
```

---

### Post by SookieLaLaLaFoe on 2014-09-27
I was under the assumption that is what the software updater is supposed to do, but no, I didn't do that from the command line.

here is my version:

LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

---

### Post by QIII on 2014-09-27
Did you tell the updater to apply the updates by clicking "Install Updates"?  Did it return any messages at all?

If not, then please start a new thread.  That is an issue with the updater not working properly, not directly about the subject of this thread.

---

### Post by SookieLaLaLaFoe on 2014-09-27
Of course, and no, got no errors. Running updates from the command line indicates all updates were applied correctly.

I posted in this thread because I though it pretty important that bash needed to be updated manually after all correct updates were applied in the manner in which most day-to-day users would apply them.

Edit: *FACEPALM* Look I know how to use the autoupdater. I'm trying to let people know that apt-get update, apt-get install -- on their own --may not be sufficient due to the dynamic nature of the bash updates being released. In my case, at the time of posting, it was *not* fixing certain variants of the bug/not installing, and that an explicit installation of bash (apt-get install -y bash) may be necessary to keep abreast of the situation -- as it was in my case. See: [http://superuser.com/a/816780](http://superuser.com/a/816780) for exact same issue on 12.04

---

### Post by deadflowr on 2014-09-27
> **kieranbool said:**
> Of course, and no, got no errors. Running updates from the command line indicates all updates were applied correctly.

I posted in this thread because I though it pretty important that bash needed to be updated manually after all correct updates were applied in the manner in which most day-to-day users would apply them.

Software updater will always give you important information about what packages are going to be updated, why, and to what version.

If, for some reason the window is too small to view the updated packages, simply hold down alt and press the middle mouse button to resize it.

You can then compare the packages you are going to install with those listed in the Ubuntu Security Notices page, I linked before, or do as I have and simply subscribe to the announcement mailing list and have all that info in you mailbox at the ready. That way you can get the notices and updates well before you read about them on some news feed. (Sorry if that sounds like a rant, isn't meant to be one)

---

### Post by Newbunto on 2014-09-28
> **JKyleOKC said:**
> it can allow the baddies to do anything they want with your machine. In itself it's just a skeleton key that unlocks total access, but once they get in the sky is their only limit.

This is overstating it.

In the best case scenario, a Ubuntu computer without this patch can still be connected to the internet in total safety.

In the medium case scenario, a Ubuntu computer for example running a vulnerable web server might allow arbitrary code execution *as the user that the web server runs as* - which may have limited consequences depending on the exact configuration - or could be a web site defacement / web site denial of service / web site password theft risk.

In the worst case scenario, it is as you say - arbitrary code execution as root - say goodbye to your computer.

The point is though that you can assess and control that level of risk by examining what software you choose to run on your computer and how you configure that software.

All that said, I agree that running a supported version of an operating system is always the safest option. So getting to an LTS version of Ubuntu ASAP is a good idea.

---

### Post by JKyleOKC on 2014-09-29
Very good points, and yes, I may have overstated things. However, many people inadvertently set up vulnerable web servers unknowingly, when they install game servers to share gaming with a few friends -- and far too many system utilities run as setuid, which means that such a vulnerable web server might then have root access from time to time without the user ever being aware of it.

Bottom line is simply that it's far too complicated a situation to be accurately described in simple terms. The best we can realistically expect is to stay as safe as we can by avoiding high-risk situations, and staying aware of the possible worst-case scenarios. Occam's Razor notwithstanding, the "simplest" solution to security problems is, far too often, wrong.

---

### Post by defaria on 2014-09-29
Can somebody tell me why my server running 13.04 is not offered an update for bash? My other systems (desktop and laptop) updated just fine. Now they are on 14.04 and I've heard that 13.04 is "end of lifed" but are the .04's supposed to be long term support, like 5 years. Doesn't that include at least security patches!?!!!

```
Defaria:echo $BASH_VERSION
4.2.45(1)-release
Defaria:grep VERSION /etc/*release
/etc/os-release:VERSION="13.04, Raring Ringtail"
/etc/os-release:VERSION_ID="13.04"
Defaria:sudo apt-get update > /dev/null 2>&1
Defaria:sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by QIII on 2014-09-29
13.04 is not LTS.  LTS releases are the April releases in even-numbered years, so 12.04 and 14.04 are current LTS releases.  13.04 is EOL and receives no more updates.

(10.04 is a special case -- it is currently under LTS support for the server version only.)

---

### Post by Lars Noodén on 2014-09-29
Version 13.04 reached end of life on January 27 this year.  The LTS versions are only every other year.  Versions 10.04 (server), 12.-04 and 14.04 are LTS.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Edit: oops , too slow  :)

---

### Post by defaria on 2014-09-29
Hmmm... I didn't know that or I misremembered it. Perhaps last time I dealt with it was 10.04... Looks like a server upgrade is in my future here...

(At least I updated bash by downloading it and compiling it).

---

### Post by deadflowr on 2014-09-29
> **defaria said:**
> Hmmm... I didn't know that or I misremembered it. Perhaps last time I dealt with it was 10.04... Looks like a server upgrade is in my future here...

(At least I updated bash by downloading it and compiling it).

If your running a 10.04 server it is still supported until April 2015.
FYI
Right now, only the three LTS server editions(10.04, 12.04, 14.04) are supported, server-wise.
10.04 desktop is dead, but the server lives on.
So there's that, maybe...

---

### Post by oygle on 2014-09-29
> **JKyleOKC said:**
> That, unfortunately, won't protect you. It's a quite subtle bug but it can allow the baddies to do anything they want with your machine. In itself it's just a skeleton key that unlocks total access, but once they get in the sky is their only limit.

I have now done a clean install of Kubuntu 14.04.1 . I have tried this ..

```
$ env 'X=() { (a)=>\' sh -c 'echo date'
date
$ 
```

Other posts have said the echo should be blank on a patched file ??

Does that mean someone has "got in" as you say, inbetween the version upgrade ?? The "Bash" DEB is bash_4.3-7ubuntu1.4_amd64.deb

---

### Post by JKyleOKC on 2014-09-29
Your test line is incomplete. Try this one, from the first page of this thread: env x='() { :;}; echo vulnerable' bash -c 'echo this is a test' 

It should return "this is a test" in any case, but if bash is vulnerable it will say "vulnerable" first.

---

### Post by oygle on 2014-09-29
Thanks very much. All looks okay, just tried it  ..

```
$ env x='() { :;}; echo vulnerable' bash -c 'echo this is a test' 
this is a test
$ 
```

---

