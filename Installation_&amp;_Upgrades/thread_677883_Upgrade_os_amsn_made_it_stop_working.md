---
title: "Upgrade os amsn made it stop working"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by franestepona on 2008-01-25
Hi guys,

I recently upgraded amsn and found an error dialog everytime i launched it. To solve the problem I installed tcl/tk 8.5-dev and then it was working again. Today I launched it and out of the blue give me this error message:

```
[16:09:32]Fran@FransMachine: amsn
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {*}$Snit_optionInfo(configure-$option)  $option]
            "
    (procedure "snit::RT.CacheConfigureCommand" line 36)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 154)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 53)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 273)

```

I have tried to reinstall and compile amsn svn, and tcl/tk CVS, but still have the same problem. Does anyone have an idea on what's going on?

Thanks!

---

