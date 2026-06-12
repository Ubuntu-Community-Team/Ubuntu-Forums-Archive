---
title: "TNEF / winmail.dat email attachment - Evolution / dev. version - HOWTO get it?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by jreinis on 2008-07-10
I saw from outlook users messages with winmail.dat attachments (TNEF **** from microsoft).

1. First question - What to say to outlook users to STOP sending such kind of attachments (I mean what to configure in outlook and outlook express settings)?

2. Second question is How to recompile development version of evolution or where to get version 2.23 64-bit for Ubuntu 8.04 Hardy Heron (apt repositories or URL links)?

2.a Am I need to uninstall regular version of evolution toward to installing development version?

Thanks.

---

### Post by freakalad on 2008-10-30
Can only provide *some* info on the winmail.dat issue: instruct OL users to not send mail in a rich(-ish) format, such as RTF or using word as their mail composer, but to stick to either straight-up TXT or HTML.
This is a problem common to OL+exchange users.

There are some online resources for decoding/decompiling these messages, but I'm always weary of those

As for evolutions compatibility, for me it's still pretty touch&go, as I us TB as my primary mail client. Apparently Evo has experimental plig-in's to deal with this, but I'm still playing around in my 64-bit environment, so I'm unable to give much more detail at this stage

Check this out for more info on this:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/247396](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/247396)

---

### Post by xfacta on 2009-05-08
Use Synaptic to install "evolution-plugins-experimental", it will also install "ytnef" and any other dependancies.
Open Evolution and go to to Edit -> Plugins and down near the bottom of the list is TNEF Attachment decoder.

This worked in Ubuntu 8.10 and I had to do it again in 9.04 after the upgrade.

We often get PDF files wrapped in tnef by Outlook and this solves it.

---

### Post by perlu on 2009-05-11
I can't get TNEF/winmail.dat attachments to open any more. Probably after the last upgrade to Jaunty. But it can also be that I have messed something up trying to solve the problem...

Internet are full with solutions th the problem, but I have not got it working. I skipped all from 2006 and the rest usually suggest to activate the "TNEF Attachment decoder" from the evolution-plugings-experimental package.

I still can not make it work! Any suggestions would be appreciated...

Thanks

Installed versions as below:

> dpkg -l evolution\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  evolution      2.26.1-0ubuntu groupware suite with mail client and organiz
ii  evolution-comm 2.26.1-0ubuntu architecture independent files for Evolution
ii  evolution-data 2.26.1-0ubuntu evolution database backend server
ii  evolution-data 2.26.1-0ubuntu architecture independent files for Evolution
un  evolution-data <none>         (no description available)
un  evolution-data <none>         (no description available)
un  evolution-dbg  <none>         (no description available)
un  evolution-docu <none>         (no description available)
ii  evolution-docu 2.26.1-0ubuntu documentation for Evolution
ii  evolution-docu 2.26.1-0ubuntu documentation for Evolution
ii  evolution-exch 2.26.0-0ubuntu Exchange plugin for the Evolution groupware 
un  evolution-exch <none>         (no description available)
ii  evolution-indi 0.1.13-0ubuntu GNOME panel indicator applet for Evolution
ii  evolution-plug 2.26.1-0ubuntu standard plugins for Evolution
ii  evolution-plug 2.26.1-0ubuntu experimental plugins for Evolution
ii  evolution-webc 2.26.0-0ubuntu webcal: URL handler for GNOME and Evolution

> dpkg -l \*ytnef\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
un  libytnef-dev          <none>                (no description available)
ii  libytnef0             1.5-1                 improved decoder for application/ms-tnef attachments
ii  libytnef0-dev         1.5-1                 improved decoder for application/ms-tnef attachments
ii  ytnef                 2.6-1ubuntu1          improved decoder for application/ms-tnef attachments

---

### Post by Lorin Ricker on 2009-05-13
For whatever it's worth:  I too get plagued by winmail.dat's from M$ users, and I found & installed, via Synergy, the **tnef** package.

No documentation on how to use, but after restarting Thunderbird, I found that highlighting the winmail.dat attachment, then right-clicking and choosing Open, an "Opening winmail.dat" dia-box pops up with "Open with /usr/bin/tnef (default)" -- click OK, and it unpacks the attachment's contents straight into my **/home/username** directory.  Neat.

More poking around:  It doesn't look like there's any configuration capabilities with tnef... I'd sure like to simply make it *unpack files into a different subdirectory*, just for neat-freak's sake.  Anyone know how to do this?  A config-file to edit?  Where?

TIA -- Lorin

---

### Post by Lorin Ricker on 2009-05-13
Hey, even better:  From Paddy Landau in [http://ubuntuforums.org/showthread.php?t=870712](http://ubuntuforums.org/showthread.php?t=870712) msg #8 --

Do you use Thunderbird? If so, install the Lookout extension:
[https://addons.mozilla.org/en-US/thunderbird/addon/4433](https://addons.mozilla.org/en-US/thunderbird/addon/4433)

This one unpacks the winmail.dat's contents right into the attachment window so you can extract 'em wherever you want.  Apparently, a winmail.dat is "kind'a like a tar file", containing what a polite (non-M$, non-Outlook) email system would simply attach as regular MIME files... see [http://kb.mozillazine.org/Winmail.dat_attachments](http://kb.mozillazine.org/Winmail.dat_attachments) -- The TB Lookout extension just unpacks the archive for us.

IMHO, asking Windoze and Outlook users to help by: Set "When sending Outlook Rich Text messages to Internet ..." to either "Convert to HTML format" or "Convert to Plain Text format"... is an exercise in futility.  Resistance is futile:  Don't ever try to teach a pig to sing.  It's a waste of your time, and it annoys the pig.

Hope this helps someone, and it definitely overrides my post immediately above.  -- Lorin

---

### Post by Orfintain on 2009-06-06
Is there a solution for evolution TNEF decoder is not working for me

---

### Post by Jofarmer on 2009-08-18
> **xfacta said:**
> Use Synaptic to install "evolution-plugins-experimental", it will also install "ytnef" and any other dependancies.
Open Evolution and go to to Edit -> Plugins and down near the bottom of the list is TNEF Attachment decoder.
This got the job done for me - Jaunty (Evolution 2.26.1)

---

### Post by sukka69 on 2009-11-06
Thanks. xfacta. Your solution works for Ubuntu 9.10. The attachment will be automatically decoded into the original attachment file format besides the winmail.dat file.

---

### Post by Orfintain on 2009-11-06
mine started working again 

thanks everyone I think I just needed to reboot after installing some of those things

---

### Post by mgmiller on 2010-06-02
I just wanted to get on file that installing evolution-plugins-experimental and then restarting evolution works properly in 64 bit Lucid (10.04).  There is nothing to configure, once you restart evolution, there will be 2 dropdowns in the email.  One has the original TNEF message attachment (winmail.dat) file and the second one will be for the pdf.  It works great.

---

### Post by airtonix on 2010-08-09
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04 LTS
Release:        10.04
Codename:       lucid

```

```

$ uname -a
Linux hostname 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

```

```
$ sudo apt-get install evolution-plugins-experimental 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution-plugins-experimental: Depends: evolution (= 2.28.3-0ubuntu9) but 2.28.3-0ubuntu10 is to be installed
E: Broken packages
```

---

