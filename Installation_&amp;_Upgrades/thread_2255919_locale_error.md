---
title: "locale error"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by anonprophet on 2014-12-08
i got this warning, when update or install
                                            
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LC_TIME = "id_ID.UTF-8",
	LC_MONETARY = "id_ID.UTF-8",
	LC_ADDRESS = "id_ID.UTF-8",
	LC_TELEPHONE = "id_ID.UTF-8",
	LC_NAME = "id_ID.UTF-8",
	LC_MEASUREMENT = "id_ID.UTF-8",
	LC_IDENTIFICATION = "id_ID.UTF-8",
	LC_NUMERIC = "id_ID.UTF-8",
	LC_PAPER = "id_ID.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

```

---

### Post by sandyd on 2014-12-08
Try
```

sudo apt-get install language-pack-en-base
```

---

