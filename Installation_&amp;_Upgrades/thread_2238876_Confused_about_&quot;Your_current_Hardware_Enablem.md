---
title: "Confused about &quot;Your current Hardware Enablement Stack (HWE) is no longer supported&quot;"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by SchnappiJedi on 2014-08-10
Confused about the following message:

Have read the link for more information and tried to do some research online. But still don't understand. Do I need to upgrade to a new HWE? I thought a LTS release was good for 5 years. Like I said, I am confused.


[I]"Your current Hardware Enablement Stack (HWE) is no longer supported
since 2014-08-07.  Security updates for critical parts (kernel
and graphics stack) of your system are no longer available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)

To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade

OR

* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty

and reboot your system."
[/I]

---

### Post by grahammechanical on 2014-08-10
This is another and possible better page to read. Look right down the page and study the charts.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The Linux kernel developers are constantly adding compatibility with new hardware to Linux. Ubuntu 12.04 is more than 2 years old. It might not be compatible with the latest hardware. It needs the improvements that have been made to Linux. So, the Ubuntu developers bring out what they call "point releases" over the first two years of an LTS period of support. So, we start with 12.04 and we get 12.04.1 and then 12.04.2 and on though 12.04.3, 12.04.4, until we are about to get 12.04.5.

New users get the point releases when they down load the ISO image. Existing 12.04 users get these point release upgrades through the usual update process. The Linux kernel in 12.04 and 12.04.1 and 12.04.5 will be supported until April 2017. But the Linux kernels in Ubuntu 12.04.2, 1204.3 and 12.04.4 are only supported up to the second week of August this year. 

Users of 12.04.2 through to 12.04.4 have choices. Upgrade to 12.04.5 or Upgrade to 14.04.1 or just upgrade the Hardware Enablement Stack. And it is this last option that is being offered and if you take my advice, ignore it. What you are being offered is an Early Preview of the HWE that will be in 12.04.5. 

I recently put in an install of Ubuuntu 12.04.4 just to test out the HWE upgrade and every went fine. But others have reported problems. Serious problems. So, I say wait until the system updates to 12.04.5. Support will continue until April 2017.

Clear? I didn't think so. :)

> [COLOR=#333333][FONT=Ubuntu Beta]will only stop receiving updates for the kernel and the graphics stack. The rest of the software will continue to get updates.[/FONT][/COLOR]

Regards.

---

### Post by kansasnoob on 2014-08-10
> **grahammechanical said:**
> This is another and possible better page to read. Look right down the page and study the charts.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The Linux kernel developers are constantly adding compatibility with new hardware to Linux. Ubuntu 12.04 is more than 2 years old. It might not be compatible with the latest hardware. It needs the improvements that have been made to Linux. So, the Ubuntu developers bring out what they call "point releases" over the first two years of an LTS period of support. So, we start with 12.04 and we get 12.04.1 and then 12.04.2 and on though 12.04.3, 12.04.4, until **[COLOR="#FF0000"]we are about to get 12.04.5[/COLOR]**.

New users get the point releases when they down load the ISO image. Existing 12.04 users get these point release upgrades through the usual update process. The Linux kernel in 12.04 and 12.04.1 and 12.04.5 will be supported until April 2017. But the Linux kernels in Ubuntu 12.04.2, 1204.3 and 12.04.4 are only supported up to the second week of August this year. 

Users of 12.04.2 through to 12.04.4 have choices. **[COLOR="#FF0000"]Upgrade to 12.04.5[/COLOR]** or Upgrade to 14.04.1 or just upgrade the Hardware Enablement Stack. And it is this last option that is being offered and **[COLOR="#FF0000"]if you take my advice, ignore it. What you are being offered is an Early Preview of the HWE that will be in 12.04.5. [/COLOR]**

I recently put in an install of Ubuuntu 12.04.4 just to test out the HWE upgrade and every went fine. But others have reported problems. Serious problems. So, I say wait until the system updates to 12.04.5. Support will continue until April 2017.

Clear? I didn't think so. :)



Regards.

You're still somewhat confused about this yourself. I highlighted the areas where you're somewhat wrong.

All Precise (12.04) users got the "upgrade" to 12.04.5 in the 'base-files' package update earlier, shortly before 12.05.5 was released on August 7th:

[https://launchpad.net/ubuntu/+source/base-files/+changelog](https://launchpad.net/ubuntu/+source/base-files/+changelog)

> base-files (6.5ubuntu6.8) precise; urgency=medium

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: [B]Bump
    version number to 12.04.5[/B] in preparation for the point release.

But that only changes the release version number, **[COLOR="#FF0000"]it does NOT change the kernel[/COLOR]** or X-stack version in any way! And **[COLOR="#FF0000"]many (almost all) kernel updates contain security related updates[/COLOR]**.

Look at this example:

[ATTACH=CONFIG]255382[/ATTACH]

You can see there that "lsb_release -a" shows I'm running 12.04.5 but the Update Manager is still showing that I need to upgrade the HWE because I'm running the Quantal series kernel, that's verified by the output of "uname -r".

If you look at the output of "cat /var/log/installer/media-info" you can see that I installed with the 12.04.2 iso, that's why I have a Quantal kernel in that Precise. Those who installed using the 12.04.3 iso will have the Raring kernel, and those who installed using the 12.04.4 iso will have the Saucy kernel. All three of those will stop receiving kernel and X-stack updates as of two days ago so **[COLOR="#FF0000"]it's not OK to just continue ignoring that warning *ad infinitum*[/COLOR]**.

I know some users are quite upset about that since they thought using an LTS would avoid such complications so we need to try very hard to see that Canonical does a much better job of messaging surrounding the whole LTS HWE EOL thing for the 14.04.2, 14.04.3, and 14.04.4 point releases. I think it could be done by simply adding an explanation just below the download link to the effect;

*[COLOR="#0000FF"]Users not requiring the absolute latest hardware support may prefer using the archived 14.04.1 installation media to avoid HWE EOL upgrades. Please take a moment to read about LTS hardware enablement here:[/COLOR]*

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Speaking of archived iso images, the 12.04.1 images are archived [here]("http://old-releases.ubuntu.com/releases/12.04.1/") and the 12.04.1 images still have the 3.2 series kernel and original Precise X-stack which are supported until April 2017 - that may be useful for some users that have older hardware that's not well supported by the Trusty kernel and X-stack.

To further complicate things release upgrade notifications should have been available no later than August 8th but someone was asleep at the wheel:

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1344762)

That should be fixed sometime tomorrow though.

So what do I recommend?

#1: Back up anything and everything important to an external source. If you haven't been doing so it's time anyway. What if your hard drive would happen to crash unexpectedly? The data you don't back up is always the data you'll lose!!!! Better safe than sorry.

#2: Create a new 14.04.1 Live DVD or USB just in case things go haywire, then try it out - first by entering the [advanced boot options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and selecting Check disc for defects to be sure it's good - then try running the live session to get some idea if Trusty is going to work with your hardware or not. Remember that whether you perform a full release upgrade or just the HWE upgrade you're still getting the Trusty kernel and X-stack.

#3: Boot back into your installed Precise session, remove the Trusty live media, and [decide which option you prefer]("https://wiki.ubuntu.com/1204_HWE_EOL#What_to_do_if_I.27m_affected.3F"). If the Trusty live session ran OK on your hardware there is a good chance that either the HWE upgrade or the full release upgrade will work, but first of all **see whether or not you're running any "Additional drivers"!** If so I highly recommend switching to the open source graphics drivers even if they don't work as well as the proprietary drivers. *Remember that the full release upgrade will not be offered until sometime on the 11th.*

**[COLOR="#FF0000"]Important warning![/COLOR]** If you dual-boot and you should have to reinstall for any reason beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I'm just full of good news, ain't I :redface:

Does that help to clear up any confusion?

---

### Post by SchnappiJedi on 2014-08-13
Honestly am only *slightly* less confused after reading this.

Do agree with one thing however...thought a LTS version was supposed to eliminate having to do anything like this in the first place....

---

