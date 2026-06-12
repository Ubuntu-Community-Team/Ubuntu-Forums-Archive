---
title: "Older versions of snap not being removed on updating to new one."
date: 2021-08-10
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-08-10
I have Flutter installed and hence while running flutter doctor I came to know this thing a few days ago (nearly 7).
Doctor summary (to see all details, run flutter doctor -v):
[&#10003;] Flutter (Channel stable, 2.2.3, on Linux, locale en_IN)
[&#10003;] Android toolchain - develop for Android devices (Android SDK version
    31.0.0-rc2)
[&#10003;] Chrome - develop for the web
[&#10003;] Android Studio (version 4.2)
[&#10003;] Android Studio (version 2020.3)
[&#10003;] IntelliJ IDEA Community Edition (version 2021.1)
[&#10003;] IntelliJ IDEA Community Edition (version 2021.2)
[&#10003;] VS Code (version 1.59.0)
[&#10003;] Connected device (1 available)

• No issues found!

Now Intellij was updated around 8 days ago. But ignored it that time  assuming to be mistake of flutter doctor. But today when I updated  android studio I also noted free space before and after. I saw free  space decreased by 1.4GB (update was of 1GB) also flutter started  showing two versions. Hence now I am confirmed that older versions are  unremoved. This didn't happen earlier.
What should I do now? I am using Ubuntu 20.04.2.

---

### Post by deadflowr on 2021-08-10
Snaps always keep a minimum of two.
You must manually remove them yourself if you want less.

---

### Post by scorp123 on 2021-08-10
> **EngineerStrange said:**
>  Hence now I am confirmed that older versions are  unremoved. This didn't happen earlier.
What should I do now? I am using Ubuntu 20.04.2.

Yes, annoying, isn't it? So I have this script to deal with this:

```

#! /bin/bash

set -eu

LANG=en_US.UTF-8 snap list --all | awk '/disabled/{print $1, $3}' | while read snapname revision; do
    sudo snap remove "$snapname" --revision="$revision"
done

```

Save this under a name that makes sense to you, e.g. **"remove-old-snaps.sh"** or something like that. Also don't forget to make it executable:

```

chmod 755 remove-old-snaps.sh

```

Afterwards you can call this script to get rid of old snaps that have the status ***"disabled"***.

---

### Post by EngineerStrange on 2021-08-11
Ok thanks a lot. Btw is this what is called as shell script?

---

