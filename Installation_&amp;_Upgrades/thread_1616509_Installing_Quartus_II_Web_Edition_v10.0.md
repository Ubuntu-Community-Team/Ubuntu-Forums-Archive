---
title: "Installing Quartus II Web Edition v10.0"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by phosphoricx on 2010-11-08
I found the solution to installing Quartus II Web Edition v10.0 on this website:
    [http://fpga4u.epfl.ch/wiki/Install_Quartus_II#Download_the_Installer_2]("http://fpga4u.epfl.ch/wiki/Install_Quartus_II#Download_the_Installer_2")

Basically the installer has a conflict with **libX11.so.6**, however there is a simple workaround.

[LIST=1]
[*]Start the installation process with "--confirm" to pause before each step
```
sh altera_installer.external.sh --confirm
Creating directory bin
Verifying archive integrity... All good.
About to extract 49568 KB in bin ... Proceed ? [Y/n] Y
Uncompressing Altera Installer............................................................................................................................
OK to execute: ./altera_installer_gui --gui  ? [Y/n]

```

[*]Delete libX11.so.6 to remove the conflict
```

cd 10.0sp1_quartus_free_linux/altera_installer/bin
rm libX11.so.6

```

[*]Continue installation process. The GUI installer should now appear.
```

OK to execute: ./altera_installer_gui --gui  ? [Y/n] Y
Fontconfig error: "conf.d", line 1: no element found
Fontconfig warning: line 73: unknown element "cachedir"
Fontconfig warning: line 74: unknown element "cachedir"

```
[/LIST]

---

### Post by dino99 on 2010-11-08
might be posted into "tutorials and tips" subforum

---

### Post by Tony_uk on 2010-11-23
Excellent.
This worked for me and I have Quartus II running nicely.

Thanks.

Tony

---

