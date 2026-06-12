---
title: "Locales Messed Up After Running Update"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by Flood-X on 2011-02-03
I ran an update today via the Update Manager (Ubuntu 10.10) and I got a bunch of error messages regarding the locales. I didn't have this problem before. So I tried uninstalling the 2nd language I have installed (Arabic) and reinstalling it. I got the same messages during the reinstall. I also tried:
sudo dpkg-reconfigure locales

and I get the same error messages:


Generating locales...
  ar_AE.UTF-8... cannot open locale definition file `ar_AE': No such file or directory
failed
  ar_BH.UTF-8... cannot open locale definition file `ar_BH': No such file or directory
failed
  ar_DZ.UTF-8... cannot open locale definition file `ar_DZ': No such file or directory
failed
  ar_EG.UTF-8... cannot open locale definition file `ar_EG': No such file or directory
failed
  ar_IN.UTF-8... cannot open locale definition file `ar_IN': No such file or directory
failed
  ar_IQ.UTF-8... cannot open locale definition file `ar_IQ': No such file or directory
failed
  ar_JO.UTF-8... cannot open locale definition file `ar_JO': No such file or directory
failed
  ar_KW.UTF-8... cannot open locale definition file `ar_KW': No such file or directory
failed
  ar_LB.UTF-8... cannot open locale definition file `ar_LB': No such file or directory
failed
  ar_LY.UTF-8... cannot open locale definition file `ar_LY': No such file or directory
failed
  ar_MA.UTF-8... cannot open locale definition file `ar_MA': No such file or directory
failed
  ar_OM.UTF-8... cannot open locale definition file `ar_OM': No such file or directory
failed
  ar_QA.UTF-8... cannot open locale definition file `ar_QA': No such file or directory
failed
  ar_SA.UTF-8... cannot open locale definition file `ar_SA': No such file or directory
failed
  ar_SD.UTF-8... cannot open locale definition file `ar_SD': No such file or directory
failed
  ar_SY.UTF-8... cannot open locale definition file `ar_SY': No such file or directory
failed
  ar_TN.UTF-8... cannot open locale definition file `ar_TN': No such file or directory
failed
  ar_YE.UTF-8... cannot open locale definition file `ar_YE': No such file or directory
failed
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... cannot open locale definition file `hi_IN': No such file or directory
failed
  en_NG.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_NZ.UTF-8... done
  en_PH.UTF-8... cannot open locale definition file `tl_PH': No such file or directory
failed
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

What is the problem and how do I fix it so that the Arabic works again?

Since the update, I no longer see Arabic as a choice in Language Support for text in menus and windows, although it appears as an installed language.

---

### Post by Flood-X on 2011-02-04
Help?

---

### Post by Flood-X on 2011-02-04
I fixed it by reinstalling the "locales" package via the Synaptic Package Manager, although I'd like to know what broke it.

---

