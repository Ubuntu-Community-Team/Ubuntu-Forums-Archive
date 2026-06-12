---
title: "vblank_mode error"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-02-21
When i run WoW via terminal or run glxgears, i get this: 

```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
```

This is my .drirc file:

```
<driconf>
    <device screen="0" driver="r600">
        <application name="Default">
            <option name="force_s3tc_enable" value="false" />
            <option name="texture_coord_units" value="8" />
            <option name="fthrottle_mode" value="2" />
            <option name="disable_stencil_two_side" value="false" />
            <option name="tcl_mode" value="3" />
            <option name="texture_depth" value="0" />
            <option name="fp_optimization" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="no_rast" value="false" />
            <option name="command_buffer_size" value="8" />
            <option name="round_mode" value="0" />
            <option name="dither_mode" value="0" />
            <option name="disable_lowimpact_fallback" value="true" />
            <option name="texture_image_units" value="8" />
            <option name="disable_s3tc" value="false" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```

As you can see, i changed **vblank_mode** to 0, but that hasnt helped, any other ideas?

Thanks
Will

---

### Post by DoeRayMe on 2010-02-22
Bump for some help :)

---

### Post by uBeer on 2010-02-22
[http://ubuntuforums.org/showpost.php?p=8735536&postcount=691](http://ubuntuforums.org/showpost.php?p=8735536&postcount=691)

Installing the 2.6.33 kernel should result in not giving the message.

---

### Post by DoeRayMe on 2010-02-22
> **uBeer said:**
> [http://ubuntuforums.org/showpost.php?p=8735536&postcount=691](http://ubuntuforums.org/showpost.php?p=8735536&postcount=691)

Installing the 2.6.33 kernel should result in not giving the message.

Thanks mate :)

---

