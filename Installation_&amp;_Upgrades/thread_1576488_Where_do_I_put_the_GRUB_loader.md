---
title: "Where do I put the GRUB loader?"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by tsam19 on 2010-09-17
This is a follow on post to one I made regarding a QUAD boot on a Macbook Pro.

Basically I'm back to the point where I've installed all 4 operating systems again.

I installed Mac OSX 1st.

Thought I'd try UNBUNTU ULTIMATE next, at this point there were 2 icons on the rEFIt boot page, Mac & Linux.

Then installed WIN 7, Linux icon disappeared & WIN XP to finalise, now showing only 3 boot icons.

However on the rEFIt boot menu I can only see 3 boot icons, the LINUx/UNBUNTU has disappeared again.

So I went back to the original installation thread & read some more posts etc & now I am going to install UNBUNTU yet again!

I've gone through all the partition settings & I have partition DEV/SDA 7 as the EXT3 for All the system files to go & DEV/SDA 6 as the SWAP FILE. - See pic

I'm quite happy & confident about those settings & sizes & orientation in the partition table.

The SWAP FILE being at the END so as to enable HIBERNATION if need be.

In the advanced section, I'm asked the BIG QUESTION  where do I install the BOOT LOADER to ???

If I didn't choose the Advanced tab & chose to install, where would the BOOT loader be installed anyway?

Thinking carefully about how the other operating systems work, It would make sense to have the BOOT LOADER installed with the system files, as do the the other operating systems.

Is it DEV/SDA 7 - Where the System files are going ?

Or is there a (HD0,???) setting which EQUATES or RELATES to DEV/SDA 7?

I'm holding off from installing until I know for sure, as good as it may be, Unbuntu has a weird install procedure.

When its installed correctly, I will see the 4 boot icons on the rEFIt boot menu.

Please only reply if you KNOW, as I'm not going to risk installing again for it to mess up the rest of the installations.

Thanks. ;) ;)

---

