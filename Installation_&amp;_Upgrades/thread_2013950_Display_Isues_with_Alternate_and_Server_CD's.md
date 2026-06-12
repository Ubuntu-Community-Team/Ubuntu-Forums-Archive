---
title: "Display Isues with Alternate and Server CD's"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by BobMarso on 2012-07-01
[FONT=Arial]First of all, I've read the displays issues sticky thread and am still having problems.

[/FONT]  [FONT=Arial]Here is my problem - I can do an install from the 64 bit Ubuntu 12.04 Desktop CD, but not the Alternate or Server CD's.  The Alternate and server CD's boot up, display the initial grep choices of "Install Ubuntu", "Install in Expert Mode", "Check CD", etc.  When I select "Install Ubuntu" or "Install in Expert Mode", the CD starts up, the screen clears, then blinks, then hangs up with alternate green and orange bars and the CD stops spinning.  However, the installation seems to continue since when I press the Enter key 5 or 6 more times (sufficient to answer the initial installation questions), the CD starts back up and the hard drives show activity.  I do not have this problem with the Desktop CD.  Using the Desktop CD, I can select "Try Ubuntu without Installing" or a straight install and have no problems.

I want to use the alternate or server Installation method since I want to set up RAID's.  

I have gone through the Displays issue sticky post and can't get past step 2.  I can press "e" to get to the Grub window and can view the default installation commands.  However when I try to edit the commands to enter the Linux /boot/vmlinux... command, the keyboard hangs up at various points, usually about 5 characters away from the end of the command I need to enter.  I only have this keyboard problem when trying to install this way.  I am able to install from the Desktop CD, install Windows Home Server, and do anything else I want with no "hung keyboard".  Why only in Grub when installing Ubuntu?

Does anyone have any idea what's going on?  I have a 4 or 5 year old ATI Radeon display adapter in my box.

Thanks in advance for the help.[/FONT]

---

### Post by BobMarso on 2012-07-02
I just found the following on the AMD/ATI support page for the Radeon 4300 series graphics family.  The link to this page is:

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

It reads as follows:

*[FONT=Arial]A  security update to the Linux kernel for vulnerability CVE-2010-3081  breaks the proprietary AMD Linux Graphics Driver. Symptoms may range  from:[/FONT]* 
[LIST]
[*]*[FONT=Arial]Severely reduced performance (no 2D or 3D acceleration) to[/FONT]*
[*]*[FONT=Arial]Complete system crashes on boot up[/FONT]*
[/LIST]
 *[FONT=Arial]Depending on the Linux distribution the problem may occur:[/FONT]*
 
[LIST]
[*]*[FONT=Arial]When rebooting after installing the security update or [/FONT]*
[*]*[FONT=Arial]When updating or reinstalling the graphics driver after installing the security update.[/FONT]*
[/LIST]
 [I][FONT=Arial]**Recommendation:**
AMD has created a hotfix to address the issue. To download and install the ATI Catalyst hotfix, click on the link below: [/FONT][/I]
 
[LIST]
[*]*[FONT=Arial][ATI Catalyst 10.9 Linux Hotfix]("https://a248.e.akamai.net/f/674/20307/1m/www2.ati.com/drivers/hotfix/catalyst_10.9_hotfix_8.773rc1/catalyst_10.9_linux_hotfix_sep27.zip")[/FONT]*
[/LIST]
 *[FONT=Arial]**Note! **This hotfix is provided as is and is not supported by AMD. It has not completed full AMD testing and is only a driver update.[/FONT]*
 [I][FONT=Arial]**Applicable Products:**
The following affected Linux distributions include, but are not limited to:[/FONT][/I]
 
[LIST]
[*]*[FONT=Arial]RHEL 5.5[/FONT]*
[*]*[FONT=Arial]openSUSE 11.3[/FONT]*
[*]*[FONT=Arial]SLED 11 SP1[/FONT]*
[*]*[FONT=Arial]SLED 10 SP3[/FONT]*
[*]*[FONT=Arial]Ubuntu 8.04[/FONT]*
[*]*[FONT=Arial]Ubuntu 9.04[/FONT]*
[*]*[FONT=Arial]Ubuntu 9.10[/FONT]*
[*]*[FONT=Arial]Ubuntu 10.04[/FONT]*
[/LIST]
 *[FONT=Arial]**Note! **Other Linux distributions and versions may  also be affected now or in the future as Linux distributors deploy the  security update for CVE-2010-3081.[/FONT]*

My problems installing 12.04 Server from the Server CD start when Ubuntu 12.04 performs the hardware check during the installation operation.  I assume the installation process installs the open source ATI driver, but how would I check if the open source driver is subject to the same problem?  Also considering my console hangs up when I try to enter grub commands (see my initial post), how would I get around this?  The AMD/ATI support page says this applies to all Radeon families from the x1000 and HD4000 up to and including the HD7000 series.  Has anyone personally installed Server 12.04 from the server CD successfully on a system using one of the above video cards?

Thanks for the help.

---

### Post by BobMarso on 2012-07-05
I'm marking this tread as solved since I now have 12.04 installed.  The solution was to not insert the installation disk until after the F2 prompt to enter BIOS was cleared from the display.  How that makes a difference I have no idea, but it works every time.

The consistent indicator that the system will boot is that the first screen to appear after the Intel boot codes in the lower right corner finish is to ask if the CD is a type 1 or type 2 CD.  If I get that prompt, I know the system will boot, not have display issues, and be able to install.

---

