---
title: "Latest Radeon Fix?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2010-09-24
There have been many many suggestions on the Forum about how to fix the open-source ATI or install proprietary AMD driver since the kernel upgrade. Today I get an update notification for fglrx. It did install. 

Proprietary Driver menu shows the fglrx is Activated [x].

Catalyst Menu won't run --> Dialog >(needs ati driver). 

Ubuntu System> Preferences> Appearance> [Visual Effects] ... A dialog box says desktop effects could not be initialized.

I think I need a configuration init ??? 

None of the installs ever put aticonfig on my system.

This is the first active fglrx I have had in the last 10 days, which is encouraging. I have had desktop options before my present troubles.

AMD64 - Asus mobo - Radeon HD 5450 

Thanks for any suggestions...

---

### Post by crl0901 on 2010-09-24
I tried activating these after a clean install of 10.04 and I couldn't get them to work.  I get a bunch of fglrx errors, so I'm staying away from them for now.

---

### Post by Unterseeboot_234 on 2010-09-25
[SIZE="4"]**Let me WARN YOU!!!**[/SIZE]

If the fglrx update does not work for your model of Radeon graphics card, and you try to fix the update or undo the update, the only alternative will be to reformat the partition. You get a Macintosh loop => broken package => fix => script returned (1) from another install => loop ...

I have spent 4 weeks on this driver issue. The card worked beautifully the first week. Now after the kernel upgrades, the card does not have any options with any driver.

I've got a very angry client. I look the fool. I don't have a decent nVidia card to swap out the orphaned HD 5450 ATI-Radeon. I don't think Ubuntu nor Radeon will ever get around to coming to my house to write me a custom driver.

==================
The beginning of the Radeon-proprietary driver failing happens this way. 
1. You do a fresh install of 10.04 Lucid. Installs in about 14 minuts.
2. You decline the pop-up to install the proprietary driver. However, under Menus System => Preferences => Appearance [ TAB ]>Visual Effects. You click the middle button to add smoother desktop functionality. That will install Radeon-proprietary driver whether you wanted it or not. You get Catalyst Control Center, fglrx, xorg-radeon ... but not jockey. This will be the best desktop my machine will ever have.

Any further upgrade to Lucid will be in ignorance of those linkages that got affected by selecting Visual Effects. If you go back to that menu, the middle button is not selected. The dialog shows None as the option for desktop enhancement. Click the Middle Button to reassure yourself you have smoother desktop effects. Ubuntu looks for available drivers, maybe it finds one to download and attempts to install -- No. Go. the error just says: failed to install.

3. The Synaptic upgrade for Radeon, the kernel patch, the blog-suggested tweaks out there on the web -- all will be a short-circuit against the driver that Appearance-menu has installed/configured previously. Jockey seems to be part of this compounding problem that happens during revision to Lucid. Indeed a re-boot takes away the good desktop effects I had previously. The latest sledge-hammer script for this Radeon driver offers no revision possible.

I don't blame Ubuntu. I don't blame AMD. They only real solution I can see is the installation CD for Lucid needs step 3 as I outlined above so xorg is linked to several buttons and the monitor as one action. But before such a dramatic change might happen, I just may get an nVidia graphic card so that I can have a their proprietary driver which links at a single phase of the lifetime of Ubuntu.

---

### Post by Unterseeboot_234 on 2010-09-27
Fifth install was the charm. I noticed when the 180+ updates listed today [ 27-Sept-2010 ] The kernel update also included the extra description '(New Install)'. I held my breath and let kernel update happen. 

It works!

It works because it left my original fglrx alone. I have a good-looking and smooth-action GUI. So...

```
for( int i = 0 ; i < Integer.MAX_VALUE; i++ ) {

     System.out.println( " Thank you Ubuntu !!! " );

}
```

---

