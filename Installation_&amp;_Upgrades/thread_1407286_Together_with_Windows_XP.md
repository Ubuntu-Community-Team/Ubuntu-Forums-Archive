---
title: "Together with Windows XP"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2010-02-15
Hi,

I installed Windows XP and then Ubuntu on the remaining disk. However, each time I go back to windows, windows decides to destroy grub and it stops loading, then I have to use a rescue disk and do a grub-install again. It's annoying to have to do this everytime I go to windows. Is there a way to avoid windows to destroy grub? Or install grub on a place windows cannot touch?

Thanks,

PMatos

---

### Post by oldfred on 2010-02-15
Do you have an HP or Dell? It may be some windows software that writes into the MBR and corrupts grub:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
HP ProtectTools and Dell Recovery Tool write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

---

### Post by recluce on 2010-02-15
Also, just for safety, I would recommend to get a live CD/DVD that includes a virus scanner, like Knoppicillin, Knoppix or a Windows UBCD and scan your MBR and Windows partitions for malware. Besides some (more or less) legitimate programs, there are malware packages that infect (and reinfect) the MBR.

Do not scan from your active Windows partition, as a system that is infected may have its virus scanner rendered ineffective as well.

---

### Post by pmatos on 2010-02-16
> **oldfred said:**
> Do you have an HP or Dell? It may be some windows software that writes into the MBR and corrupts grub:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
HP ProtectTools and Dell Recovery Tool write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

Argh, it's the stupid HP ProtectTools that my company uses on Windows then.

Thank you very much for the exhaustive list of refs posted!

---

### Post by dE_logics on 2010-02-16
> However, each time I go back to windows, windows decides to destroy grub and it stops loading

Sounds like new Microsoft stratagy...Wipe everything *nix.

---

