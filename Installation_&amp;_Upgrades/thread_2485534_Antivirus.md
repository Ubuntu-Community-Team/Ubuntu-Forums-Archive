---
title: "Antivirus"
date: 2023-04-01
forum: Installation &amp; Upgrades
---

### Post by skywalker007 on 2023-04-01
What would you advise as the best antivirus / antimalware software to install. I would prefer one that has a GUI that also has reliable updates to keep the system very clean as I am going to start working for a company where I will use my laptop a lot on their network.

This is important because as far as I am aware there are one or two of the servers using linux, the rest and the workstations are obviously using windows. 
They have antivirus on their windows but I am not sure if they have antivirus on the linux servers.

And if you know, where can I download it from?
Just to keep them safe... and no one saying "it was your fault"

Thanks
Johan

---

### Post by TheFu on 2023-04-01
AV vendors have trained MS-Windows users to think they are "protected" by installing one and letting it use 20% of the system.
Linux has a different architecture, so the typical types of malware are different.  Nothing replaces a smart user, clicking and typing. It cannot.

Also, desktop viruses really don't have much use on Linux, so the sorts of attacks are less about 1 individual and more about taking over the entire OS.  If you don't have network services open to the world, you've effectively stopped most of the Unix malware.

The best security tool that I know is offline, versioned, backups.  Not some tool claiming to catch 30% of all Windows viruses.

The only time I've run AV on Linux was when it was required by E&O Insurance.  It was useless.

If you want to give someone your money, ESET is a reputable tool, I suppose.  I've never used it.
On Linux, people who work in mixed environments where they share documents with MS-Windows users/computers could be helped by running ClamAV on their storage server where files are kept. I wouldn't run it on a desktop.  95% of what ClamAV signatures find are MS-Windows viruses that would likely NOT harm a single user's files on Linux.

Versioned backups that are offline, taken daily or weekly, are the main tool you should be seeking. There are some subtle things in creating the backups and the retention period for each version will be key.  For example, more and more companies are finding that crackers penetrate their network, but don't do anything to be caught for many, many, months.  That means we need to have at least that many versioned backups.  

Don't worry, since versioned backups aren't like cans of tomatoes.  We don't need 1 can for each backup.  We need 1 can initially, then diffs off those versions. Some backup tools are smarter than others.  They take very little in each daily backup and those daily backups take just a few minutes to complete.  On my high-risk systems, I keep a year of daily, versioned, backups.  For lower-risk system, the minimal retention period is 90 days.

If you follow the _Basic Ubuntu Security Guidelines_ and follow the sticky threads at the top of the Ubuntu Security sub-forum here, [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338) , there is little to worry about, assuming you aren't doing high risk activities on the systems involved.
That doesn't mean we are free to do anything we like, regardless of risk. But it does mean if you follow the recommendations, have offline, versioned, backups, that if you are ever cracked, recovery will be an inconvenience, but no data will be lost.  Computer security is all about risk mitigation to a level we need for our attack profile, but not 1% more.

---

### Post by ian-weisser on 2023-04-02
Excellent summary of good security practices. Listen to it.

You could pay serious money to a security consultant...who will tell you essentially the same thing, but less clearly.

---

### Post by DuckHook on 2023-04-02
> **ian-weisser said:**
> Excellent summary of good security practices. Listen to it.

You could pay serious money to a security consultant...who will tell you essentially the same thing, but less clearly.
I ***have*** paid serious money to not just one, but a few security consultants. Sadly, they did not tell me the same thing, though the clarity was, as you astutely observe, seriously muddled.

Security consultants come in all shapes and sizes I suppose, so that may account for my bad experiences. The more likely explanation is that we were a completely Windows shop at the time. For security consultants, Windows is the goose that lays golden eggs. Why would they want to kill it?

Perhaps some detail is in order:

My security consultants recommended exactly the concoction of antivirus-antimalware-antihistamines-antibiotics-anti&#8209;inflammatories regimen that Windows users have been conditioned to think of as "solutions". They also recommended silly things like enforced monthly password changes&#8212;measures that we now know to be more harmful than helpful. They were the reason why our workstations all had little stickies plastered on monitors with our users' passwords written down in the clear.

It was only after my retirement and my coming to appreciate Linux that I realized that my security consultants were promoting selective disinformation and limited options. What we should have been doing was moving our servers to Linux and keeping as little critical data on Windows machines as possible. Perhaps even Windows thin clients. If you are going to dumb down, may as well go all the way. What we were advised instead was to increase our reliance on Windows but to fill in Windows' shortcomings with a dog's breakfast of aftermarket third party tools. TheFu is not kidding when he says that 20% of system resources was wasted on running all of that bloated antiware.

The other problem was that it was necessary. When running Windows, one would be a fool indeed not to run AV. The fact that Linux does not require AV was never even breathed much less discussed. There is a large element of self&#8209;serving self&#8209;preservation in security consultants not promoting Linux. Why raise the possibility of a solution that might solve you out of a job?

@skywalker007

If you are going to work for a company in a consulting or employment capacity and will be hooking into their internal network, then what is important is to get their policies and procedures in writing from them. Then stick to those policies and procedures like your career depends on it, because it does. It is not enough to ask on these forums because we have no idea what the company's requirements are.

If it were me, I would never hook my laptop into their network. I would insist on a laptop from their IT department, filled with their anti&#8209;apps, encrypted to their standards, and then I would not install a single additional thing on that laptop that wasn't already there. Nor would I do a single shred of work on that machine that was personal or not work related. In other words, draw a very clear line between your personal gear and whatever gear they want you to work on. That is the only way to avoid the "it was your fault" exposure.

If the company requires you to run anti&#8209;blah&#8209;blah&#8209;blah, then run anti&#8209;blah&#8209;blah&#8209;blah. If the company requires you to change your password every month, then change your password every month. If the company requires you to burn offerings to the computing gods, then burn offerings to the computing gods.

Do what they tell you to do, not what we or any other forum tells you to do.

---

### Post by DuckHook on 2023-04-02
Further thoughts:

If your new employer does not have a formal written IT policy, then it's time for some serious career reassessment.

Even worse, if you employer actually allows you to use your own gear on their internal LAN, then you really must take stock of your situation and either alert them to their insanity or start looking for alternative employment, because any such organization is just a disaster waiting to happen.

I know of no organization today, even small Mom and Pop shops, that allow outside computers to hook into their internal systems. Moreover, in our modern world, any company doing anything at all will be handling other people's data. Not a week goes by that we don't get reports of yet another trove of personal data being released into the dark web because some consultant was allowed to download the company's entire database onto their laptop which was then either hacked or stolen. Those companies will sometimes get sued into bankruptcy (not often enough, in my opinion), so if you work for a company with such lax security, you should be concerned enough to have plan "B"s in place.

---

### Post by mIk3_08 on 2023-04-02
> **DuckHook said:**
> Further thoughts:
If your new employer does not have a formal written IT policy, then it's time for some serious career reassessment.

> **ian-weisser said:**
> Excellent summary of good security practices. Listen to it.
You could pay serious money to a security consultant...who will tell you essentially the same thing, but less clearly.
> **TheFu said:**
> AV vendors have trained MS-Windows users to think  they are "protected" by installing one and letting it use 20% of the  system.
Linux has a different architecture, so the typical types of malware are  different.  Nothing replaces a smart user, clicking and typing. It  cannot.

I absolutely 101% AGREE with this people. They are already ELITE in this nature of system and they are working with this environment for many decade now. I have nothing left to hide. Their are proven and tested already. Regards and cheers.

---

### Post by ActionParsnip on 2023-04-03
ClamAV is decent

---

### Post by TheFu on 2023-04-03
> **ActionParsnip said:**
> ClamAV is decent

It it constantly complaining about outdated signatures or outdated version of the code.  To work, it needs both to be updated and for whatever reason, that doesn't happen all the time.  There are often weeks between when a new version of the signatures is provided, but the version of the code in the repos doesn't match.  There is some overlap, but that overlap isn't long enough, IME.  Sometimes it is.  Sometimes it isn't.

Security Consultants have to meet "industry standards".  Companies who are hacked are let off the hook if they meet "standard industry practices", regardless of whether they are effective or not.  Think of any large companies that have been hacked, even if they haven't followed "industry standards". None have been held accountable for their failures.

---

### Post by xinuzi on 2023-04-06
Maybe also check your firewall with ```
sudo ufw status
```.

---

### Post by TheFu on 2023-04-06
There are multiple interfaces into the Linux firewall. UFW is just one.  iptables and nftables are the core utilities.  It is possible NOT to use UFW, yet still have a set of firewall rules.  On Ubuntu, no firewall is enabled by default. When we (the admin for a system) enables any network service, that person is expected to configure the firewall of their choice to protect that service. It isn't automatic.

iptables has been around a very long time. With Ubuntu 22.04 and later, nftables is an option. I don't know if it is the default, but I don't think so.  Admins and users don't really touch the linux firewall directly. We use interface tools to ask it to do what we need.

On desktops, there's a GUI for UFW, gufw.  With a default DENY in/ALLOW all out, and allowing inbound LAN access, that would be secure enough for most home users on desktops.  For laptops, having a HOME and AWAY profile for gufw is smart, since when we are "away", we'd want to block all inbound, even from the same subnet on our laptops.

For a stronger firewall stance, block all inbound from anywhere and block all outbound to anywhere, then manually add the exact, specific, rules you want to allow System A to talk with System B and C and D and E.  This can be a hassle very quickly.

There's another "application firewall" available on Linux now, that was modeled after a MacOS tool.  I can't remember the name ... let me search ... OpenSnitch.  Some reading on that:
[https://itsfoss.com/opensnitch-firewall-linux/](https://itsfoss.com/opensnitch-firewall-linux/)
[https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/](https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/)
I think most Mac and Windows people would like OpenSnitch better than the more traditional linux filewalls.

---

### Post by xinuzi on 2023-04-15
> **TheFu said:**
> There are multiple interfaces into the Linux firewall. UFW is just one.  iptables and nftables are the core utilities.  It is possible NOT to use UFW, yet still have a set of firewall rules.  On Ubuntu, no firewall is enabled by default. When we (the admin for a system) enables any network service, that person is expected to configure the firewall of their choice to protect that service. It isn't automatic.

iptables has been around a very long time. With Ubuntu 22.04 and later, nftables is an option. I don't know if it is the default, but I don't think so.  Admins and users don't really touch the linux firewall directly. We use interface tools to ask it to do what we need.

On desktops, there's a GUI for UFW, gufw.  With a default DENY in/ALLOW all out, and allowing inbound LAN access, that would be secure enough for most home users on desktops.  For laptops, having a HOME and AWAY profile for gufw is smart, since when we are "away", we'd want to block all inbound, even from the same subnet on our laptops.

For a stronger firewall stance, block all inbound from anywhere and block all outbound to anywhere, then manually add the exact, specific, rules you want to allow System A to talk with System B and C and D and E.  This can be a hassle very quickly.

There's another "application firewall" available on Linux now, that was modeled after a MacOS tool.  I can't remember the name ... let me search ... OpenSnitch.  Some reading on that:
[https://itsfoss.com/opensnitch-firewall-linux/](https://itsfoss.com/opensnitch-firewall-linux/)
[https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/](https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/)
I think most Mac and Windows people would like OpenSnitch better than the more traditional linux filewalls.

Nice.
Could this also be explanable to Ordinary People in Common Language?

---

### Post by xinuzi on 2023-04-15
[URL="https://youtu.be/OVgaQa--NLM"]https://youtu.be/OVgaQa--NLM


O.M.G., So Simple & So Enerving!
[/URL]

---

### Post by TheFu on 2023-04-15
> **xinuzi said:**
> Nice.
Could this also be explanable to Ordinary People in Common Language?

Sure. Give it a try.

---

### Post by wyattwhiteeagle on 2023-09-25
Looks like some good, old-fashioned, straight-forward, and sound advice here.
Thank you all.

---

