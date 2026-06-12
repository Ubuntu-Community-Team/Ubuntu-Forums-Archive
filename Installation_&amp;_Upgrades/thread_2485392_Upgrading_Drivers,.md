---
title: "Upgrading Drivers,"
date: 2023-03-28
forum: Installation &amp; Upgrades
---

### Post by themeal on 2023-03-28
I was installing driver and this happened 
"Traceback (most recent call last):
  File "/usr/bin/ubuntu-drivers", line 513, in <module>
    greet()
  File "/usr/lib/python3/dist-packages/click/core.py", line 1128, in __call__
    return self.main(*args, **kwargs)
  File "/usr/lib/python3/dist-packages/click/core.py", line 1053, in main
    rv = self.invoke(ctx)
  File "/usr/lib/python3/dist-packages/click/core.py", line 1659, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/usr/lib/python3/dist-packages/click/core.py", line 1395, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/usr/lib/python3/dist-packages/click/core.py", line 754, in invoke
    return __callback(*args, **kwargs)
  File "/usr/lib/python3/dist-packages/click/decorators.py", line 84, in new_func
    return ctx.invoke(f, obj, *args, **kwargs)
  File "/usr/lib/python3/dist-packages/click/core.py", line 754, in invoke
    return __callback(*args, **kwargs)
  File "/usr/bin/ubuntu-drivers", line 413, in install
    command_install(config)
  File "/usr/bin/ubuntu-drivers", line 187, in command_install
    UbuntuDrivers.detect.nvidia_desktop_pre_installation_hook(to_install)
  File "/usr/lib/python3/dist-packages/UbuntuDrivers/detect.py", line 839, in nvidia_desktop_pre_installation_hook
    with_nvidia_kms = version >= 470
UnboundLocalError: local variable 'version' referenced before assignment"
How do i fix this?

---

### Post by MAFoElffen on 2023-03-28
First go back to Post #1. Select Edit Post > Go Advanced > Select the raw output to highlight it... > Select the "#" Icon to wrap that text with CODE Tags.

What was the exact command that you entered? I wasn't there seeing over your shoulder, so, I need more info.

I am assuming something like this
```

sudo ubuntu-drivers <option>
# most likely: sudo ubuntu-drivers install

```
It looks like it failed while looking for NVidia information...

Could you please either run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") from the Forum's GitHub, or add the [system-info PPA]("https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info")  to install it and run it... When it asks to upload, says Yes, and copy down the PasteBin URL, to post here. That way we can see your system information and config, in a way that Linux see's your system. That way we can see what we are trying to recommend a solution for, the current Linux kernel, what drivers it is currently using for which Video hardware...

Then do this and post the output _"within" CODE Tags_... That step is important. Raw output and commands posted without using CODE Tags does strange things to the forums software.
```

sudo ubuntu-drivers list

```

---

