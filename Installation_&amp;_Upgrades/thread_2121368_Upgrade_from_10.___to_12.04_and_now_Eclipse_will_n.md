---
title: "Upgrade from 10.__ to 12.04 and now Eclipse will not start"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by raequin on 2013-03-01
I upgraded (twice --- first from 10.04 to 11.10, then immediately to 12.04 (I think those numbers are right)) and when I went to run Eclipse for the first time since the upgrade I got an error:

"An error has occurred. See the log file
/home/raequin/.eclipse/org.eclipse.platform_3.7.0_155965261/configuration/1362172481340.log."

I'm looking for help with how to get it running again.  I know nothing!  Here is the log file:

```
!SESSION 2013-03-01 16:05:59.018 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.6.0_26
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 0 2013-03-01 16:06:00.405
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.405
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface.text_3.7.2.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-01 16:06:00.405
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.405
!MESSAGE Bundle reference:file:plugins/org.eclipse.ui_3.7.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-01 16:06:00.405
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.405
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface.databinding_1.5.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-01 16:06:00.405
!MESSAGE Missing required bundle org.eclipse.swt_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.405
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface_3.7.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface 2 0 2013-03-01 16:06:00.406
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.406
!MESSAGE Bundle reference:file:plugins/org.eclipse.ui.workbench_3.7.1.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-01 16:06:00.406
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2013-03-01 16:06:00.494
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.494
!MESSAGE Bundle org.eclipse.compare_3.5.202.dist [15] was not resolved.
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-01 16:06:00.494
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.494
!MESSAGE Bundle org.eclipse.debug.ui_3.7.102.dist [40] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui.console_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing imported package org.eclipse.ui.forms.widgets_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.495
!MESSAGE Bundle org.eclipse.equinox.p2.ui_2.1.1.dist [86] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui_3.6.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.equinox.security.ui_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.495
!MESSAGE Bundle org.eclipse.equinox.p2.ui.importexport_1.0.1.dist [87] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing required bundle org.eclipse.ui.forms_3.5.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.dialogs_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.model_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-01 16:06:00.495
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.viewers_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.495
!MESSAGE Bundle org.eclipse.equinox.p2.ui.sdk_1.0.200.dist [88] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.ui_3.6.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing optionally required bundle org.eclipse.compare_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.496
!MESSAGE Bundle org.eclipse.equinox.p2.ui.sdk.scheduler_1.0.100.dist [89] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.actions_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.query_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing imported package org.eclipse.equinox.p2.ui_[2.0.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.496
!MESSAGE Bundle org.eclipse.equinox.security.ui_1.1.0.dist [95] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.security.ui 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.ui_[3.4.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.496
!MESSAGE Bundle org.eclipse.help.ui_3.5.101.dist [101] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.help.ui 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.496
!MESSAGE Bundle org.eclipse.jface_3.7.0.dist [104] was not resolved.
!SUBENTRY 2 org.eclipse.jface 2 0 2013-03-01 16:06:00.496
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.496
!MESSAGE Bundle org.eclipse.jface.databinding_1.5.0.dist [105] was not resolved.
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.swt_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.jface_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.497
!MESSAGE Bundle org.eclipse.jface.text_3.7.2.dist [106] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.497
!MESSAGE Bundle org.eclipse.jsch.ui_1.1.300.dist [108] was not resolved.
!SUBENTRY 2 org.eclipse.jsch.ui 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.497
!MESSAGE Bundle org.eclipse.ltk.ui.refactoring_3.6.0.dist [110] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.200,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.compare_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.team.ui_[3.4.100,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.497
!MESSAGE Bundle org.eclipse.platform_3.7.2.dist [113] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui.intro_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing optionally required bundle org.eclipse.ui.cheatsheets_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing optionally required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing optionally required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.497
!MESSAGE Bundle org.eclipse.search_3.7.0.dist [116] was not resolved.
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.497
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.498
!MESSAGE Bundle org.eclipse.team.cvs.ui_3.3.401.dist [121] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.jface.text_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.ui.workbench.texteditor_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.ui.editors_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.console_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.team.ui_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.compare_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.498
!MESSAGE Bundle org.eclipse.team.ui_3.6.101.dist [122] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.compare_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-01 16:06:00.498
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui_3.7.0.dist [124] was not resolved.
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui.workbench_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui.browser_3.3.101.dist [125] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui.cheatsheets_3.4.100.dist [126] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing optionally required bundle org.eclipse.help.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui.console_3.5.100.dist [127] was not resolved.
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui.editors_3.7.0.dist [128] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.7.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.499
!MESSAGE Bundle org.eclipse.ui.externaltools_3.2.0.dist [129] was not resolved.
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-01 16:06:00.499
!MESSAGE Missing required bundle org.eclipse.debug.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.forms_3.5.101.dist [130] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.jface_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.forms 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing optionally required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.ide_3.7.0.dist [131] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui.workbench_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing optionally required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.ide.application_1.0.300.dist [132] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.application 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide.application 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.intro_3.4.100.dist [133] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.intro 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.intro.universal_3.2.500.dist [134] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.universal 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.intro.universal 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui.intro_[3.4.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.navigator_3.5.101.dist [135] was not resolved.
!SUBENTRY 2 org.eclipse.ui.navigator 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.500
!MESSAGE Bundle org.eclipse.ui.navigator.resources_3.4.300.dist [136] was not resolved.
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.500
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.jface_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui.views.properties.tabbed_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.net_1.2.100.dist [137] was not resolved.
!SUBENTRY 2 org.eclipse.ui.net 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.presentations.r21_3.2.200.dist [138] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.views_3.6.0.dist [139] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.views.properties.tabbed_3.5.200.dist [140] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.ui_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.workbench_3.7.1.dist [141] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.jface.databinding_[1.3.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.workbench.compatibility_3.2.100.dist [142] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.compatibility 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing host org.eclipse.ui.workbench_[3.0.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.501
!MESSAGE Bundle org.eclipse.ui.workbench.texteditor_3.7.0.dist [143] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor 2 0 2013-03-01 16:06:00.501
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor 2 0 2013-03-01 16:06:00.502
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.502
!MESSAGE Bundle org.eclipse.update.scheduler_3.2.300.dist [147] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler 2 0 2013-03-01 16:06:00.502
!MESSAGE Missing required bundle org.eclipse.update.ui_[3.1.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.scheduler 2 0 2013-03-01 16:06:00.502
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-01 16:06:00.502
!MESSAGE Bundle org.eclipse.update.ui_3.2.300.dist [148] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui 2 0 2013-03-01 16:06:00.502
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.ui 2 0 2013-03-01 16:06:00.502
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 4 0 2013-03-01 16:06:00.503
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry. The applications available are: org.eclipse.ant.core.antRunner, org.eclipse.equinox.app.error, org.eclipse.equinox.p2.director, org.eclipse.equinox.p2.garbagecollector.application, org.eclipse.equinox.p2.publisher.InstallPublisher, org.eclipse.equinox.p2.publisher.EclipseGenerator, org.eclipse.equinox.p2.publisher.ProductPublisher, org.eclipse.equinox.p2.publisher.FeaturesAndBundlesPublisher, org.eclipse.equinox.p2.reconciler.application, org.eclipse.equinox.p2.repository.repo2runnable, org.eclipse.equinox.p2.repository.metadataverifier, org.eclipse.equinox.p2.artifact.repository.mirrorApplication, org.eclipse.equinox.p2.metadata.repository.mirrorApplication, org.eclipse.equinox.p2.updatesite.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.CategoryPublisher, org.eclipse.help.base.infocenterApplication, org.eclipse.help.base.helpApplication, org.eclipse.help.base.indexTool, org.eclipse.jdt.core.JavaCodeFormatter, org.eclipse.update.core.standaloneUpdate, org.eclipse.update.core.siteOptimizer.
	at org.eclipse.equinox.internal.app.EclipseAppContainer.startDefaultApp(EclipseAppContainer.java:248)
	at org.eclipse.equinox.internal.app.MainApplicationLauncher.run(MainApplicationLauncher.java:29)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1410)

```

---

### Post by MAFoElffen on 2013-03-02
I do Ubuntu v12.10 64 and Eclipse 3.8

One of the first errors was that a jar file didn't run and it was boinked from there on.

And extract from my config:
```

...
java.runtime.name=Java(TM) SE Runtime Environment
java.runtime.version=1.7.0_15-b03
java.specification.name=Java Platform API Specification
java.specification.vendor=Oracle Corporation
java.specification.version=1.7
java.vendor=Oracle Corporation
java.vendor.url=http://java.oracle.com/
java.vendor.url.bug=http://bugreport.sun.com/bugreport/
java.version=1.7.0_15
java.vm.info=mixed mode
java.vm.name=Java HotSpot(TM) 64-Bit Server VM
java.vm.specification.name=Java Virtual Machine Specification
java.vm.specification.vendor=Oracle Corporation
java.vm.specification.version=1.7
java.vm.vendor=Oracle Corporation
java.vm.version=23.7-b01
...

```
Notice that "Openjdk" is not there and they want the Sun or Oracle jre, spec'ed by vendor and version...

I have Openjdk-7 and IcedTea installed, but I also have the oracle 7 jdk installed, withthe included Oracle JRE installed --but-- instead of removing other java versions, I installed Oracle as an "alternate" java (supplemental). That way everything runs fine with the Openjdk JRE and all it's installed hooks and pluggins...But if something does spec "by vendor," the Sun/Oracle JRE version is then called.

Even if you had the sun java jre installed before from the repo's... It used to be an Ubuntu package in their repo's. Then, remember? Oracle bought out Sun and they got funny about "licensing." It's still a freebie, but because of the licensing, it is not in the main repo any longer... So your old sun java jre package from Ubuntu- dead-ended and was not upgraded in do-release-upgrade's.

---

### Post by raequin on 2013-03-04
I upgraded to OpenJDK 7.  Eclipse still would not start.  I completely removed Eclipse via Synaptic Package Manager, and reinstalled it.  I still get an error at startup.  Here's the log file.

```
!SESSION 2013-03-04 09:55:23.349 -----------------------------------------------
eclipse.buildId=I20110613-1736
java.version=1.6.0_27
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 0 2013-03-04 09:55:28.567
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.567
!MESSAGE Bundle reference:file:plugins/org.eclipse.ui.workbench_3.7.1.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-04 09:55:28.567
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.568
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface_3.7.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface 2 0 2013-03-04 09:55:28.568
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.568
!MESSAGE Bundle reference:file:plugins/org.eclipse.ui_3.7.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-04 09:55:28.568
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.568
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface.text_3.7.2.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-04 09:55:28.568
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.568
!MESSAGE Bundle reference:file:plugins/org.eclipse.jface.databinding_1.5.0.dist.jar was not resolved.
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-04 09:55:28.568
!MESSAGE Missing required bundle org.eclipse.swt_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2013-03-04 09:55:28.653
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.653
!MESSAGE Bundle org.eclipse.compare_3.5.202.dist [15] was not resolved.
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.compare 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.653
!MESSAGE Bundle org.eclipse.debug.ui_3.7.102.dist [40] was not resolved.
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.console_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.debug.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing imported package org.eclipse.ui.forms.widgets_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.653
!MESSAGE Bundle org.eclipse.equinox.p2.ui_2.1.1.dist [86] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui_3.6.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.equinox.security.ui_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.653
!MESSAGE Bundle org.eclipse.equinox.p2.ui.importexport_1.0.1.dist [87] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing required bundle org.eclipse.ui.forms_3.5.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.653
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.dialogs_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.model_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.importexport 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.viewers_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.equinox.p2.ui.sdk_1.0.200.dist [88] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui_3.6.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing optionally required bundle org.eclipse.compare_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.equinox.p2.ui.sdk.scheduler_1.0.100.dist [89] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.equinox.p2.ui_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.actions_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing imported package org.eclipse.equinox.internal.p2.ui.query_0.0.0.
!SUBENTRY 2 org.eclipse.equinox.p2.ui.sdk.scheduler 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing imported package org.eclipse.equinox.p2.ui_[2.0.0,3.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.equinox.security.ui_1.1.0.dist [95] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.security.ui 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui_[3.4.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.help.ui_3.5.101.dist [101] was not resolved.
!SUBENTRY 2 org.eclipse.help.ui 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.help.ui 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.jface_3.7.0.dist [104] was not resolved.
!SUBENTRY 2 org.eclipse.jface 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.jface.databinding_1.5.0.dist [105] was not resolved.
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.swt_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.jface.databinding 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.jface_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.jface.text_3.7.2.dist [106] was not resolved.
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.swt_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.jface.text 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.654
!MESSAGE Bundle org.eclipse.jsch.ui_1.1.300.dist [108] was not resolved.
!SUBENTRY 2 org.eclipse.jsch.ui 2 0 2013-03-04 09:55:28.654
!MESSAGE Missing required bundle org.eclipse.ui_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.655
!MESSAGE Bundle org.eclipse.ltk.ui.refactoring_3.6.0.dist [110] was not resolved.
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.200,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.compare_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ltk.ui.refactoring 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.team.ui_[3.4.100,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.655
!MESSAGE Bundle org.eclipse.platform_3.7.2.dist [113] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.intro_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.cheatsheets_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.platform 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.655
!MESSAGE Bundle org.eclipse.search_3.7.0.dist [116] was not resolved.
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.search 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.655
!MESSAGE Bundle org.eclipse.team.cvs.ui_3.3.401.dist [121] was not resolved.
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.jface.text_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.workbench.texteditor_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing optionally required bundle org.eclipse.ui.editors_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.655
!MESSAGE Missing required bundle org.eclipse.ui.console_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.team.ui_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.compare_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.cvs.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.team.ui_3.6.101.dist [122] was not resolved.
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.compare_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.team.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.editors_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.ui_3.7.0.dist [124] was not resolved.
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.workbench_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.ui.browser_3.3.101.dist [125] was not resolved.
!SUBENTRY 2 org.eclipse.ui.browser 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.ui.cheatsheets_3.4.100.dist [126] was not resolved.
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.cheatsheets 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing optionally required bundle org.eclipse.help.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.ui.console_3.5.100.dist [127] was not resolved.
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.console 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.656
!MESSAGE Bundle org.eclipse.ui.editors_3.7.0.dist [128] was not resolved.
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-04 09:55:28.656
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.editors 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.7.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.externaltools_3.2.0.dist [129] was not resolved.
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing optionally required bundle org.eclipse.ui.ide_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.externaltools 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.debug.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.forms_3.5.101.dist [130] was not resolved.
!SUBENTRY 2 org.eclipse.ui.forms 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.jface_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.forms 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing optionally required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.ide_3.7.0.dist [131] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui.workbench_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing optionally required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing optionally required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.ide.application_1.0.300.dist [132] was not resolved.
!SUBENTRY 2 org.eclipse.ui.ide.application 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.ide.application 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.intro_3.4.100.dist [133] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.intro 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.intro.universal_3.2.500.dist [134] was not resolved.
!SUBENTRY 2 org.eclipse.ui.intro.universal 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.intro.universal 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui.intro_[3.4.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.657
!MESSAGE Bundle org.eclipse.ui.navigator_3.5.101.dist [135] was not resolved.
!SUBENTRY 2 org.eclipse.ui.navigator 2 0 2013-03-04 09:55:28.657
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.navigator.resources_3.4.300.dist [136] was not resolved.
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.ide_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.jface_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.navigator_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.views.properties.tabbed_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.workbench.texteditor_[3.6.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.navigator.resources 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ltk.ui.refactoring_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.net_1.2.100.dist [137] was not resolved.
!SUBENTRY 2 org.eclipse.ui.net 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.presentations.r21_3.2.200.dist [138] was not resolved.
!SUBENTRY 2 org.eclipse.ui.presentations.r21 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.views_3.6.0.dist [139] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.views.properties.tabbed_3.5.200.dist [140] was not resolved.
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui.views_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.views.properties.tabbed 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.3.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.workbench_3.7.1.dist [141] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.jface_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.swt_[3.5.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.jface.databinding_[1.3.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.workbench.compatibility_3.2.100.dist [142] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.compatibility 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing host org.eclipse.ui.workbench_[3.0.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.ui.workbench.texteditor_3.7.0.dist [143] was not resolved.
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.jface.text_[3.7.0,4.0.0).
!SUBENTRY 2 org.eclipse.ui.workbench.texteditor 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.ui_[3.5.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.658
!MESSAGE Bundle org.eclipse.update.scheduler_3.2.300.dist [147] was not resolved.
!SUBENTRY 2 org.eclipse.update.scheduler 2 0 2013-03-04 09:55:28.658
!MESSAGE Missing required bundle org.eclipse.update.ui_[3.1.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.scheduler 2 0 2013-03-04 09:55:28.659
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-03-04 09:55:28.659
!MESSAGE Bundle org.eclipse.update.ui_3.2.300.dist [148] was not resolved.
!SUBENTRY 2 org.eclipse.update.ui 2 0 2013-03-04 09:55:28.659
!MESSAGE Missing required bundle org.eclipse.ui_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.ui 2 0 2013-03-04 09:55:28.659
!MESSAGE Missing required bundle org.eclipse.ui.forms_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 4 0 2013-03-04 09:55:28.660
!MESSAGE Application error
!STACK 1
java.lang.RuntimeException: Application "org.eclipse.ui.ide.workbench" could not be found in the registry. The applications available are: org.eclipse.ant.core.antRunner, org.eclipse.equinox.app.error, org.eclipse.equinox.p2.director, org.eclipse.equinox.p2.garbagecollector.application, org.eclipse.equinox.p2.publisher.InstallPublisher, org.eclipse.equinox.p2.publisher.EclipseGenerator, org.eclipse.equinox.p2.publisher.ProductPublisher, org.eclipse.equinox.p2.publisher.FeaturesAndBundlesPublisher, org.eclipse.equinox.p2.reconciler.application, org.eclipse.equinox.p2.repository.repo2runnable, org.eclipse.equinox.p2.repository.metadataverifier, org.eclipse.equinox.p2.artifact.repository.mirrorApplication, org.eclipse.equinox.p2.metadata.repository.mirrorApplication, org.eclipse.equinox.p2.updatesite.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.UpdateSitePublisher, org.eclipse.equinox.p2.publisher.CategoryPublisher, org.eclipse.help.base.infocenterApplication, org.eclipse.help.base.helpApplication, org.eclipse.help.base.indexTool, org.eclipse.jdt.core.JavaCodeFormatter, org.eclipse.update.core.standaloneUpdate, org.eclipse.update.core.siteOptimizer.
	at org.eclipse.equinox.internal.app.EclipseAppContainer.startDefaultApp(EclipseAppContainer.java:248)
	at org.eclipse.equinox.internal.app.MainApplicationLauncher.run(MainApplicationLauncher.java:29)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1410)
```

Why does "java.version" and "java.vendor" in the log file not reflect the fact that I installed OpenJDK7?  I appreciate any help.

---

### Post by raequin on 2013-03-25
This is no longer an issue.  I downloaded Eclipse from eclipse.org and installed it into my home directory.  Also, I set the default java to openjdk 7 using this command:

[code]sudo update-alternatives --config java[\code].

---

