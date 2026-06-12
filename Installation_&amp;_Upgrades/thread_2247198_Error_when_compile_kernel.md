---
title: "Error when compile kernel"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by john303 on 2014-10-06
after update kernel
```
inux-3.8.13/sound/soc/ux500/Makefile
linux-3.8.13/sound/soc/ux500/mop500.c
linux-3.8.13/sound/soc/ux500/mop500_ab8500.c
linux-3.8.13/sound/soc/ux500/mop500_ab8500.h
linux-3.8.13/sound/soc/ux500/ux500_msp_dai.c
linux-3.8.13/sound/soc/ux500/ux500_msp_dai.h
linux-3.8.13/sound/soc/ux500/ux500_msp_i2s.c
linux-3.8.13/sound/soc/ux500/ux500_msp_i2s.h
linux-3.8.13/sound/soc/ux500/ux500_pcm.c
linux-3.8.13/sound/soc/ux500/ux500_pcm.h
linux-3.8.13/sound/sound_core.c
linux-3.8.13/sound/sound_firmware.c
linux-3.8.13/sound/sparc/
linux-3.8.13/sound/sparc/Kconfig
linux-3.8.13/sound/sparc/Makefile
linux-3.8.13/sound/sparc/amd7930.c
linux-3.8.13/sound/sparc/cs4231.c
linux-3.8.13/sound/sparc/dbri.c
linux-3.8.13/sound/spi/
linux-3.8.13/sound/spi/Kconfig
linux-3.8.13/sound/spi/Makefile
linux-3.8.13/sound/spi/at73c213.c
linux-3.8.13/sound/spi/at73c213.h
linux-3.8.13/sound/synth/
linux-3.8.13/sound/synth/Makefile
linux-3.8.13/sound/synth/emux/
linux-3.8.13/sound/synth/emux/Makefile
linux-3.8.13/sound/synth/emux/emux.c
linux-3.8.13/sound/synth/emux/emux_effect.c
linux-3.8.13/sound/synth/emux/emux_hwdep.c
linux-3.8.13/sound/synth/emux/emux_nrpn.c
linux-3.8.13/sound/synth/emux/emux_oss.c
linux-3.8.13/sound/synth/emux/emux_proc.c
linux-3.8.13/sound/synth/emux/emux_seq.c
linux-3.8.13/sound/synth/emux/emux_synth.c
linux-3.8.13/sound/synth/emux/emux_voice.h
linux-3.8.13/sound/synth/emux/soundfont.c
linux-3.8.13/sound/synth/util_mem.c
linux-3.8.13/sound/usb/
linux-3.8.13/sound/usb/6fire/
linux-3.8.13/sound/usb/6fire/Makefile
linux-3.8.13/sound/usb/6fire/chip.c
linux-3.8.13/sound/usb/6fire/chip.h
linux-3.8.13/sound/usb/6fire/comm.c
linux-3.8.13/sound/usb/6fire/comm.h
linux-3.8.13/sound/usb/6fire/common.h
linux-3.8.13/sound/usb/6fire/control.c
linux-3.8.13/sound/usb/6fire/control.h
linux-3.8.13/sound/usb/6fire/firmware.c
linux-3.8.13/sound/usb/6fire/firmware.h
linux-3.8.13/sound/usb/6fire/midi.c
linux-3.8.13/sound/usb/6fire/midi.h
linux-3.8.13/sound/usb/6fire/pcm.c
linux-3.8.13/sound/usb/6fire/pcm.h
linux-3.8.13/sound/usb/Kconfig
linux-3.8.13/sound/usb/Makefile
linux-3.8.13/sound/usb/caiaq/
linux-3.8.13/sound/usb/caiaq/Makefile
linux-3.8.13/sound/usb/caiaq/audio.c
linux-3.8.13/sound/usb/caiaq/audio.h
linux-3.8.13/sound/usb/caiaq/control.c
linux-3.8.13/sound/usb/caiaq/control.h
linux-3.8.13/sound/usb/caiaq/device.c
linux-3.8.13/sound/usb/caiaq/device.h
linux-3.8.13/sound/usb/caiaq/input.c
linux-3.8.13/sound/usb/caiaq/input.h
linux-3.8.13/sound/usb/caiaq/midi.c
linux-3.8.13/sound/usb/caiaq/midi.h
linux-3.8.13/sound/usb/card.c
linux-3.8.13/sound/usb/card.h
linux-3.8.13/sound/usb/clock.c
linux-3.8.13/sound/usb/clock.h
linux-3.8.13/sound/usb/debug.h
linux-3.8.13/sound/usb/endpoint.c
linux-3.8.13/sound/usb/endpoint.h
linux-3.8.13/sound/usb/format.c
linux-3.8.13/sound/usb/format.h
linux-3.8.13/sound/usb/helper.c
linux-3.8.13/sound/usb/helper.h
linux-3.8.13/sound/usb/midi.c
linux-3.8.13/sound/usb/midi.h
linux-3.8.13/sound/usb/misc/
linux-3.8.13/sound/usb/misc/Makefile
linux-3.8.13/sound/usb/misc/ua101.c
linux-3.8.13/sound/usb/mixer.c
linux-3.8.13/sound/usb/mixer.h
linux-3.8.13/sound/usb/mixer_maps.c
linux-3.8.13/sound/usb/mixer_quirks.c
linux-3.8.13/sound/usb/mixer_quirks.h
linux-3.8.13/sound/usb/pcm.c
linux-3.8.13/sound/usb/pcm.h
linux-3.8.13/sound/usb/power.h
linux-3.8.13/sound/usb/proc.c
linux-3.8.13/sound/usb/proc.h
linux-3.8.13/sound/usb/quirks-table.h
linux-3.8.13/sound/usb/quirks.c
linux-3.8.13/sound/usb/quirks.h
linux-3.8.13/sound/usb/stream.c
linux-3.8.13/sound/usb/stream.h
linux-3.8.13/sound/usb/usbaudio.h
linux-3.8.13/sound/usb/usx2y/
linux-3.8.13/sound/usb/usx2y/Makefile
linux-3.8.13/sound/usb/usx2y/us122l.c
linux-3.8.13/sound/usb/usx2y/us122l.h
linux-3.8.13/sound/usb/usx2y/usX2Yhwdep.c
linux-3.8.13/sound/usb/usx2y/usX2Yhwdep.h
linux-3.8.13/sound/usb/usx2y/usb_stream.c
linux-3.8.13/sound/usb/usx2y/usb_stream.h
linux-3.8.13/sound/usb/usx2y/usbus428ctldefs.h
linux-3.8.13/sound/usb/usx2y/usbusx2y.c
linux-3.8.13/sound/usb/usx2y/usbusx2y.h
linux-3.8.13/sound/usb/usx2y/usbusx2yaudio.c
linux-3.8.13/sound/usb/usx2y/usx2y.h
linux-3.8.13/sound/usb/usx2y/usx2yhwdeppcm.c
linux-3.8.13/sound/usb/usx2y/usx2yhwdeppcm.h
linux-3.8.13/tools/
linux-3.8.13/tools/Makefile
linux-3.8.13/tools/firewire/
linux-3.8.13/tools/firewire/Makefile
linux-3.8.13/tools/firewire/decode-fcp.c
linux-3.8.13/tools/firewire/list.h
linux-3.8.13/tools/firewire/nosy-dump.c
linux-3.8.13/tools/firewire/nosy-dump.h
linux-3.8.13/tools/hv/
linux-3.8.13/tools/hv/hv_get_dhcp_info.sh
linux-3.8.13/tools/hv/hv_get_dns_info.sh
linux-3.8.13/tools/hv/hv_kvp_daemon.c
linux-3.8.13/tools/hv/hv_set_ifconfig.sh
linux-3.8.13/tools/include/
linux-3.8.13/tools/include/tools/
linux-3.8.13/tools/include/tools/be_byteshift.h
linux-3.8.13/tools/include/tools/le_byteshift.h
linux-3.8.13/tools/lguest/
linux-3.8.13/tools/lguest/.gitignore
linux-3.8.13/tools/lguest/Makefile
linux-3.8.13/tools/lguest/extract
linux-3.8.13/tools/lguest/lguest.c
linux-3.8.13/tools/lguest/lguest.txt
linux-3.8.13/tools/lib/
linux-3.8.13/tools/lib/traceevent/
linux-3.8.13/tools/lib/traceevent/.gitignore
linux-3.8.13/tools/lib/traceevent/Makefile
linux-3.8.13/tools/lib/traceevent/event-parse.c
linux-3.8.13/tools/lib/traceevent/event-parse.h
linux-3.8.13/tools/lib/traceevent/event-utils.h
linux-3.8.13/tools/lib/traceevent/parse-filter.c
linux-3.8.13/tools/lib/traceevent/parse-utils.c
linux-3.8.13/tools/lib/traceevent/trace-seq.c
linux-3.8.13/tools/nfsd/
linux-3.8.13/tools/nfsd/inject_fault.sh
linux-3.8.13/tools/perf/
linux-3.8.13/tools/perf/.gitignore
linux-3.8.13/tools/perf/CREDITS
linux-3.8.13/tools/perf/Documentation/
linux-3.8.13/tools/perf/Documentation/Makefile
linux-3.8.13/tools/perf/Documentation/android.txt
linux-3.8.13/tools/perf/Documentation/asciidoc.conf
linux-3.8.13/tools/perf/Documentation/examples.txt
linux-3.8.13/tools/perf/Documentation/jit-interface.txt
linux-3.8.13/tools/perf/Documentation/manpage-1.72.xsl
linux-3.8.13/tools/perf/Documentation/manpage-base.xsl
linux-3.8.13/tools/perf/Documentation/manpage-bold-literal.xsl
linux-3.8.13/tools/perf/Documentation/manpage-normal.xsl
linux-3.8.13/tools/perf/Documentation/manpage-suppress-sp.xsl
linux-3.8.13/tools/perf/Documentation/perf-annotate.txt
linux-3.8.13/tools/perf/Documentation/perf-archive.txt
linux-3.8.13/tools/perf/Documentation/perf-bench.txt
linux-3.8.13/tools/perf/Documentation/perf-buildid-cache.txt
linux-3.8.13/tools/perf/Documentation/perf-buildid-list.txt
linux-3.8.13/tools/perf/Documentation/perf-diff.txt
linux-3.8.13/tools/perf/Documentation/perf-evlist.txt
linux-3.8.13/tools/perf/Documentation/perf-help.txt
linux-3.8.13/tools/perf/Documentation/perf-inject.txt
linux-3.8.13/tools/perf/Documentation/perf-kmem.txt
linux-3.8.13/tools/perf/Documentation/perf-kvm.txt
linux-3.8.13/tools/perf/Documentation/perf-list.txt
linux-3.8.13/tools/perf/Documentation/perf-lock.txt
linux-3.8.13/tools/perf/Documentation/perf-probe.txt
linux-3.8.13/tools/perf/Documentation/perf-record.txt
linux-3.8.13/tools/perf/Documentation/perf-report.txt
linux-3.8.13/tools/perf/Documentation/perf-sched.txt
linux-3.8.13/tools/perf/Documentation/perf-script-perl.txt
linux-3.8.13/tools/perf/Documentation/perf-script-python.txt
linux-3.8.13/tools/perf/Documentation/perf-script.txt
linux-3.8.13/tools/perf/Documentation/perf-stat.txt
linux-3.8.13/tools/perf/Documentation/perf-test.txt
linux-3.8.13/tools/perf/Documentation/perf-timechart.txt
linux-3.8.13/tools/perf/Documentation/perf-top.txt
linux-3.8.13/tools/perf/Documentation/perf-trace.txt
linux-3.8.13/tools/perf/Documentation/perf.txt
linux-3.8.13/tools/perf/Documentation/perfconfig.example
linux-3.8.13/tools/perf/MANIFEST
linux-3.8.13/tools/perf/Makefile
linux-3.8.13/tools/perf/arch/
linux-3.8.13/tools/perf/arch/arm/
linux-3.8.13/tools/perf/arch/arm/Makefile
linux-3.8.13/tools/perf/arch/arm/util/
linux-3.8.13/tools/perf/arch/arm/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/common.c
linux-3.8.13/tools/perf/arch/common.h
linux-3.8.13/tools/perf/arch/powerpc/
linux-3.8.13/tools/perf/arch/powerpc/Makefile
linux-3.8.13/tools/perf/arch/powerpc/util/
linux-3.8.13/tools/perf/arch/powerpc/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/powerpc/util/header.c
linux-3.8.13/tools/perf/arch/s390/
linux-3.8.13/tools/perf/arch/s390/Makefile
linux-3.8.13/tools/perf/arch/s390/util/
linux-3.8.13/tools/perf/arch/s390/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/sh/
linux-3.8.13/tools/perf/arch/sh/Makefile
linux-3.8.13/tools/perf/arch/sh/util/
linux-3.8.13/tools/perf/arch/sh/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/sparc/
linux-3.8.13/tools/perf/arch/sparc/Makefile
linux-3.8.13/tools/perf/arch/sparc/util/
linux-3.8.13/tools/perf/arch/sparc/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/x86/
linux-3.8.13/tools/perf/arch/x86/Makefile
linux-3.8.13/tools/perf/arch/x86/include/
linux-3.8.13/tools/perf/arch/x86/include/perf_regs.h
linux-3.8.13/tools/perf/arch/x86/util/
linux-3.8.13/tools/perf/arch/x86/util/dwarf-regs.c
linux-3.8.13/tools/perf/arch/x86/util/header.c
linux-3.8.13/tools/perf/arch/x86/util/unwind.c
linux-3.8.13/tools/perf/bash_completion
linux-3.8.13/tools/perf/bench/
linux-3.8.13/tools/perf/bench/bench.h
linux-3.8.13/tools/perf/bench/mem-memcpy-arch.h
linux-3.8.13/tools/perf/bench/mem-memcpy-x86-64-asm-def.h
linux-3.8.13/tools/perf/bench/mem-memcpy-x86-64-asm.S
linux-3.8.13/tools/perf/bench/mem-memcpy.c
linux-3.8.13/tools/perf/bench/mem-memset-arch.h
linux-3.8.13/tools/perf/bench/mem-memset-x86-64-asm-def.h
linux-3.8.13/tools/perf/bench/mem-memset-x86-64-asm.S
linux-3.8.13/tools/perf/bench/mem-memset.c
linux-3.8.13/tools/perf/bench/sched-messaging.c
linux-3.8.13/tools/perf/bench/sched-pipe.c
linux-3.8.13/tools/perf/builtin-annotate.c
linux-3.8.13/tools/perf/builtin-bench.c
linux-3.8.13/tools/perf/builtin-buildid-cache.c
linux-3.8.13/tools/perf/builtin-buildid-list.c
linux-3.8.13/tools/perf/builtin-diff.c
linux-3.8.13/tools/perf/builtin-evlist.c
linux-3.8.13/tools/perf/builtin-help.c
linux-3.8.13/tools/perf/builtin-inject.c
linux-3.8.13/tools/perf/builtin-kmem.c
linux-3.8.13/tools/perf/builtin-kvm.c
linux-3.8.13/tools/perf/builtin-list.c
linux-3.8.13/tools/perf/builtin-lock.c
linux-3.8.13/tools/perf/builtin-probe.c
linux-3.8.13/tools/perf/builtin-record.c
linux-3.8.13/tools/perf/builtin-report.c
linux-3.8.13/tools/perf/builtin-sched.c
linux-3.8.13/tools/perf/builtin-script.c
linux-3.8.13/tools/perf/builtin-stat.c
linux-3.8.13/tools/perf/builtin-timechart.c
linux-3.8.13/tools/perf/builtin-top.c
linux-3.8.13/tools/perf/builtin-trace.c
linux-3.8.13/tools/perf/builtin.h
linux-3.8.13/tools/perf/command-list.txt
linux-3.8.13/tools/perf/config/
linux-3.8.13/tools/perf/config/feature-tests.mak
linux-3.8.13/tools/perf/config/utilities.mak
linux-3.8.13/tools/perf/design.txt
linux-3.8.13/tools/perf/perf-archive.sh
linux-3.8.13/tools/perf/perf.c
linux-3.8.13/tools/perf/perf.h
linux-3.8.13/tools/perf/python/
linux-3.8.13/tools/perf/python/twatch.py
linux-3.8.13/tools/perf/scripts/
linux-3.8.13/tools/perf/scripts/perl/
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/Context.c
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/Context.xs
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/Makefile.PL
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/README
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/Perf/
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/Perf/Trace/
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/Perf/Trace/Context.pm
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/Perf/Trace/Core.pm
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/lib/Perf/Trace/Util.pm
linux-3.8.13/tools/perf/scripts/perl/Perf-Trace-Util/typemap
linux-3.8.13/tools/perf/scripts/perl/bin/
linux-3.8.13/tools/perf/scripts/perl/bin/check-perf-trace-record
linux-3.8.13/tools/perf/scripts/perl/bin/failed-syscalls-record
linux-3.8.13/tools/perf/scripts/perl/bin/failed-syscalls-report
linux-3.8.13/tools/perf/scripts/perl/bin/rw-by-file-record
linux-3.8.13/tools/perf/scripts/perl/bin/rw-by-file-report
linux-3.8.13/tools/perf/scripts/perl/bin/rw-by-pid-record
linux-3.8.13/tools/perf/scripts/perl/bin/rw-by-pid-report
linux-3.8.13/tools/perf/scripts/perl/bin/rwtop-record
linux-3.8.13/tools/perf/scripts/perl/bin/rwtop-report
linux-3.8.13/tools/perf/scripts/perl/bin/wakeup-latency-record
linux-3.8.13/tools/perf/scripts/perl/bin/wakeup-latency-report
linux-3.8.13/tools/perf/scripts/perl/bin/workqueue-stats-record
linux-3.8.13/tools/perf/scripts/perl/bin/workqueue-stats-report
linux-3.8.13/tools/perf/scripts/perl/check-perf-trace.pl
linux-3.8.13/tools/perf/scripts/perl/failed-syscalls.pl
linux-3.8.13/tools/perf/scripts/perl/rw-by-file.pl
linux-3.8.13/tools/perf/scripts/perl/rw-by-pid.pl
linux-3.8.13/tools/perf/scripts/perl/rwtop.pl
linux-3.8.13/tools/perf/scripts/perl/wakeup-latency.pl
linux-3.8.13/tools/perf/scripts/perl/workqueue-stats.pl
linux-3.8.13/tools/perf/scripts/python/
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/Context.c
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/Trace/
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/Trace/Core.py
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/Trace/EventClass                                                                                .py
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/Trace/SchedGui.p                                                                                y
linux-3.8.13/tools/perf/scripts/python/Perf-Trace-Util/lib/Perf/Trace/Util.py
linux-3.8.13/tools/perf/scripts/python/bin/
linux-3.8.13/tools/perf/scripts/python/bin/event_analyzing_sample-record
linux-3.8.13/tools/perf/scripts/python/bin/event_analyzing_sample-report
linux-3.8.13/tools/perf/scripts/python/bin/failed-syscalls-by-pid-record
linux-3.8.13/tools/perf/scripts/python/bin/failed-syscalls-by-pid-report
linux-3.8.13/tools/perf/scripts/python/bin/futex-contention-record
linux-3.8.13/tools/perf/scripts/python/bin/futex-contention-report
linux-3.8.13/tools/perf/scripts/python/bin/net_dropmonitor-record
linux-3.8.13/tools/perf/scripts/python/bin/net_dropmonitor-report
linux-3.8.13/tools/perf/scripts/python/bin/netdev-times-record
linux-3.8.13/tools/perf/scripts/python/bin/netdev-times-report
linux-3.8.13/tools/perf/scripts/python/bin/sched-migration-record
linux-3.8.13/tools/perf/scripts/python/bin/sched-migration-report
linux-3.8.13/tools/perf/scripts/python/bin/sctop-record
linux-3.8.13/tools/perf/scripts/python/bin/sctop-report
linux-3.8.13/tools/perf/scripts/python/bin/syscall-counts-by-pid-record
linux-3.8.13/tools/perf/scripts/python/bin/syscall-counts-by-pid-report
linux-3.8.13/tools/perf/scripts/python/bin/syscall-counts-record
linux-3.8.13/tools/perf/scripts/python/bin/syscall-counts-report
linux-3.8.13/tools/perf/scripts/python/check-perf-trace.py
linux-3.8.13/tools/perf/scripts/python/event_analyzing_sample.py
linux-3.8.13/tools/perf/scripts/python/failed-syscalls-by-pid.py
linux-3.8.13/tools/perf/scripts/python/futex-contention.py
linux-3.8.13/tools/perf/scripts/python/net_dropmonitor.py
linux-3.8.13/tools/perf/scripts/python/netdev-times.py
linux-3.8.13/tools/perf/scripts/python/sched-migration.py
linux-3.8.13/tools/perf/scripts/python/sctop.py
linux-3.8.13/tools/perf/scripts/python/syscall-counts-by-pid.py
linux-3.8.13/tools/perf/scripts/python/syscall-counts.py
linux-3.8.13/tools/perf/tests/
linux-3.8.13/tools/perf/tests/attr.c
linux-3.8.13/tools/perf/tests/attr.py
linux-3.8.13/tools/perf/tests/attr/
linux-3.8.13/tools/perf/tests/attr/README
linux-3.8.13/tools/perf/tests/attr/base-record
linux-3.8.13/tools/perf/tests/attr/base-stat
linux-3.8.13/tools/perf/tests/attr/test-record-basic
linux-3.8.13/tools/perf/tests/attr/test-record-branch-any
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-any
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-any_call
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-any_ret
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-hv
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-ind_call
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-k
linux-3.8.13/tools/perf/tests/attr/test-record-branch-filter-u
linux-3.8.13/tools/perf/tests/attr/test-record-count
linux-3.8.13/tools/perf/tests/attr/test-record-data
linux-3.8.13/tools/perf/tests/attr/test-record-freq
linux-3.8.13/tools/perf/tests/attr/test-record-graph-default
linux-3.8.13/tools/perf/tests/attr/test-record-graph-dwarf
linux-3.8.13/tools/perf/tests/attr/test-record-graph-fp
linux-3.8.13/tools/perf/tests/attr/test-record-group
linux-3.8.13/tools/perf/tests/attr/test-record-group1
linux-3.8.13/tools/perf/tests/attr/test-record-no-delay
linux-3.8.13/tools/perf/tests/attr/test-record-no-inherit
linux-3.8.13/tools/perf/tests/attr/test-record-no-samples
linux-3.8.13/tools/perf/tests/attr/test-record-period
linux-3.8.13/tools/perf/tests/attr/test-record-raw
linux-3.8.13/tools/perf/tests/attr/test-stat-basic
linux-3.8.13/tools/perf/tests/attr/test-stat-default
linux-3.8.13/tools/perf/tests/attr/test-stat-detailed-1
linux-3.8.13/tools/perf/tests/attr/test-stat-detailed-2
linux-3.8.13/tools/perf/tests/attr/test-stat-detailed-3
linux-3.8.13/tools/perf/tests/attr/test-stat-group
linux-3.8.13/tools/perf/tests/attr/test-stat-group1
linux-3.8.13/tools/perf/tests/attr/test-stat-no-inherit
linux-3.8.13/tools/perf/tests/builtin-test.c
linux-3.8.13/tools/perf/tests/dso-data.c
linux-3.8.13/tools/perf/tests/evsel-roundtrip-name.c
linux-3.8.13/tools/perf/tests/evsel-tp-sched.c
linux-3.8.13/tools/perf/tests/mmap-basic.c
linux-3.8.13/tools/perf/tests/open-syscall-all-cpus.c
linux-3.8.13/tools/perf/tests/open-syscall-tp-fields.c
linux-3.8.13/tools/perf/tests/open-syscall.c
linux-3.8.13/tools/perf/tests/parse-events.c
linux-3.8.13/tools/perf/tests/perf-record.c
linux-3.8.13/tools/perf/tests/pmu.c
linux-3.8.13/tools/perf/tests/rdpmc.c
linux-3.8.13/tools/perf/tests/tests.h
linux-3.8.13/tools/perf/tests/util.c
linux-3.8.13/tools/perf/tests/vmlinux-kallsyms.c
linux-3.8.13/tools/perf/ui/
linux-3.8.13/tools/perf/ui/browser.c
linux-3.8.13/tools/perf/ui/browser.h
linux-3.8.13/tools/perf/ui/browsers/
linux-3.8.13/tools/perf/ui/browsers/annotate.c
linux-3.8.13/tools/perf/ui/browsers/hists.c
linux-3.8.13/tools/perf/ui/browsers/map.c
linux-3.8.13/tools/perf/ui/browsers/map.h
linux-3.8.13/tools/perf/ui/browsers/scripts.c
linux-3.8.13/tools/perf/ui/gtk/
linux-3.8.13/tools/perf/ui/gtk/browser.c
linux-3.8.13/tools/perf/ui/gtk/gtk.h
linux-3.8.13/tools/perf/ui/gtk/helpline.c
linux-3.8.13/tools/perf/ui/gtk/progress.c
linux-3.8.13/tools/perf/ui/gtk/setup.c
linux-3.8.13/tools/perf/ui/gtk/util.c
linux-3.8.13/tools/perf/ui/helpline.c
linux-3.8.13/tools/perf/ui/helpline.h
linux-3.8.13/tools/perf/ui/hist.c
linux-3.8.13/tools/perf/ui/keysyms.h
linux-3.8.13/tools/perf/ui/libslang.h
linux-3.8.13/tools/perf/ui/progress.c
linux-3.8.13/tools/perf/ui/progress.h
linux-3.8.13/tools/perf/ui/setup.c
linux-3.8.13/tools/perf/ui/stdio/
linux-3.8.13/tools/perf/ui/stdio/hist.c
linux-3.8.13/tools/perf/ui/tui/
linux-3.8.13/tools/perf/ui/tui/helpline.c
linux-3.8.13/tools/perf/ui/tui/progress.c
linux-3.8.13/tools/perf/ui/tui/setup.c
linux-3.8.13/tools/perf/ui/tui/util.c
linux-3.8.13/tools/perf/ui/ui.h
linux-3.8.13/tools/perf/ui/util.c
linux-3.8.13/tools/perf/ui/util.h
linux-3.8.13/tools/perf/util/
linux-3.8.13/tools/perf/util/PERF-VERSION-GEN
linux-3.8.13/tools/perf/util/abspath.c
linux-3.8.13/tools/perf/util/alias.c
linux-3.8.13/tools/perf/util/annotate.c
linux-3.8.13/tools/perf/util/annotate.h
linux-3.8.13/tools/perf/util/bitmap.c
linux-3.8.13/tools/perf/util/build-id.c
linux-3.8.13/tools/perf/util/build-id.h
linux-3.8.13/tools/perf/util/cache.h
linux-3.8.13/tools/perf/util/callchain.c
linux-3.8.13/tools/perf/util/callchain.h
linux-3.8.13/tools/perf/util/cgroup.c
linux-3.8.13/tools/perf/util/cgroup.h
linux-3.8.13/tools/perf/util/color.c
linux-3.8.13/tools/perf/util/color.h
linux-3.8.13/tools/perf/util/config.c
linux-3.8.13/tools/perf/util/cpumap.c
linux-3.8.13/tools/perf/util/cpumap.h
linux-3.8.13/tools/perf/util/ctype.c
linux-3.8.13/tools/perf/util/debug.c
linux-3.8.13/tools/perf/util/debug.h
linux-3.8.13/tools/perf/util/debugfs.c
linux-3.8.13/tools/perf/util/debugfs.h
linux-3.8.13/tools/perf/util/dso.c
linux-3.8.13/tools/perf/util/dso.h
linux-3.8.13/tools/perf/util/dwarf-aux.c
linux-3.8.13/tools/perf/util/dwarf-aux.h
linux-3.8.13/tools/perf/util/environment.c
linux-3.8.13/tools/perf/util/event.c
linux-3.8.13/tools/perf/util/event.h
linux-3.8.13/tools/perf/util/evlist.c
linux-3.8.13/tools/perf/util/evlist.h
linux-3.8.13/tools/perf/util/evsel.c
linux-3.8.13/tools/perf/util/evsel.h
linux-3.8.13/tools/perf/util/exec_cmd.c
linux-3.8.13/tools/perf/util/exec_cmd.h
linux-3.8.13/tools/perf/util/generate-cmdlist.sh
linux-3.8.13/tools/perf/util/header.c
linux-3.8.13/tools/perf/util/header.h
linux-3.8.13/tools/perf/util/help.c
linux-3.8.13/tools/perf/util/help.h
linux-3.8.13/tools/perf/util/hist.c
linux-3.8.13/tools/perf/util/hist.h
linux-3.8.13/tools/perf/util/hweight.c
linux-3.8.13/tools/perf/util/include/
linux-3.8.13/tools/perf/util/include/asm/
linux-3.8.13/tools/perf/util/include/asm/alternative-asm.h
linux-3.8.13/tools/perf/util/include/asm/asm-offsets.h
linux-3.8.13/tools/perf/util/include/asm/bug.h
linux-3.8.13/tools/perf/util/include/asm/byteorder.h
linux-3.8.13/tools/perf/util/include/asm/cpufeature.h
linux-3.8.13/tools/perf/util/include/asm/dwarf2.h
linux-3.8.13/tools/perf/util/include/asm/hweight.h
linux-3.8.13/tools/perf/util/include/asm/swab.h
linux-3.8.13/tools/perf/util/include/asm/system.h
linux-3.8.13/tools/perf/util/include/asm/uaccess.h
linux-3.8.13/tools/perf/util/include/asm/unistd_32.h
linux-3.8.13/tools/perf/util/include/asm/unistd_64.h
linux-3.8.13/tools/perf/util/include/dwarf-regs.h
linux-3.8.13/tools/perf/util/include/linux/
linux-3.8.13/tools/perf/util/include/linux/bitmap.h
linux-3.8.13/tools/perf/util/include/linux/bitops.h
linux-3.8.13/tools/perf/util/include/linux/compiler.h
linux-3.8.13/tools/perf/util/include/linux/const.h
linux-3.8.13/tools/perf/util/include/linux/ctype.h
linux-3.8.13/tools/perf/util/include/linux/export.h
linux-3.8.13/tools/perf/util/include/linux/hash.h
linux-3.8.13/tools/perf/util/include/linux/kernel.h
linux-3.8.13/tools/perf/util/include/linux/linkage.h
linux-3.8.13/tools/perf/util/include/linux/list.h
linux-3.8.13/tools/perf/util/include/linux/magic.h
linux-3.8.13/tools/perf/util/include/linux/poison.h
linux-3.8.13/tools/perf/util/include/linux/prefetch.h
linux-3.8.13/tools/perf/util/include/linux/rbtree.h
linux-3.8.13/tools/perf/util/include/linux/rbtree_augmented.h
linux-3.8.13/tools/perf/util/include/linux/string.h
linux-3.8.13/tools/perf/util/include/linux/types.h
linux-3.8.13/tools/perf/util/intlist.c
linux-3.8.13/tools/perf/util/intlist.h
linux-3.8.13/tools/perf/util/levenshtein.c
linux-3.8.13/tools/perf/util/levenshtein.h
linux-3.8.13/tools/perf/util/machine.c
linux-3.8.13/tools/perf/util/machine.h
linux-3.8.13/tools/perf/util/map.c
linux-3.8.13/tools/perf/util/map.h
linux-3.8.13/tools/perf/util/pager.c
linux-3.8.13/tools/perf/util/parse-events.c
linux-3.8.13/tools/perf/util/parse-events.h
linux-3.8.13/tools/perf/util/parse-events.l
linux-3.8.13/tools/perf/util/parse-events.y
linux-3.8.13/tools/perf/util/parse-options.c
linux-3.8.13/tools/perf/util/parse-options.h
linux-3.8.13/tools/perf/util/path.c
linux-3.8.13/tools/perf/util/perf_regs.h
linux-3.8.13/tools/perf/util/pmu.c
linux-3.8.13/tools/perf/util/pmu.h
linux-3.8.13/tools/perf/util/pmu.l
linux-3.8.13/tools/perf/util/pmu.y
linux-3.8.13/tools/perf/util/probe-event.c
linux-3.8.13/tools/perf/util/probe-event.h
linux-3.8.13/tools/perf/util/probe-finder.c
linux-3.8.13/tools/perf/util/probe-finder.h
linux-3.8.13/tools/perf/util/pstack.c
linux-3.8.13/tools/perf/util/pstack.h
linux-3.8.13/tools/perf/util/python-ext-sources
linux-3.8.13/tools/perf/util/python.c
linux-3.8.13/tools/perf/util/quote.c
linux-3.8.13/tools/perf/util/quote.h
linux-3.8.13/tools/perf/util/rblist.c
linux-3.8.13/tools/perf/util/rblist.h
linux-3.8.13/tools/perf/util/run-command.c
linux-3.8.13/tools/perf/util/run-command.h
linux-3.8.13/tools/perf/util/scripting-engines/
linux-3.8.13/tools/perf/util/scripting-engines/trace-event-perl.c
linux-3.8.13/tools/perf/util/scripting-engines/trace-event-python.c
linux-3.8.13/tools/perf/util/session.c
linux-3.8.13/tools/perf/util/session.h
linux-3.8.13/tools/perf/util/setup.py
linux-3.8.13/tools/perf/util/sigchain.c
linux-3.8.13/tools/perf/util/sigchain.h
linux-3.8.13/tools/perf/util/sort.c
linux-3.8.13/tools/perf/util/sort.h
linux-3.8.13/tools/perf/util/stat.c
linux-3.8.13/tools/perf/util/stat.h
linux-3.8.13/tools/perf/util/strbuf.c
linux-3.8.13/tools/perf/util/strbuf.h
linux-3.8.13/tools/perf/util/strfilter.c
linux-3.8.13/tools/perf/util/strfilter.h
linux-3.8.13/tools/perf/util/string.c
linux-3.8.13/tools/perf/util/strlist.c
linux-3.8.13/tools/perf/util/strlist.h
linux-3.8.13/tools/perf/util/svghelper.c
linux-3.8.13/tools/perf/util/svghelper.h
linux-3.8.13/tools/perf/util/symbol-elf.c
linux-3.8.13/tools/perf/util/symbol-minimal.c
linux-3.8.13/tools/perf/util/symbol.c
linux-3.8.13/tools/perf/util/symbol.h
linux-3.8.13/tools/perf/util/sysfs.c
linux-3.8.13/tools/perf/util/sysfs.h
linux-3.8.13/tools/perf/util/target.c
linux-3.8.13/tools/perf/util/target.h
linux-3.8.13/tools/perf/util/thread.c
linux-3.8.13/tools/perf/util/thread.h
linux-3.8.13/tools/perf/util/thread_map.c
linux-3.8.13/tools/perf/util/thread_map.h
linux-3.8.13/tools/perf/util/tool.h
linux-3.8.13/tools/perf/util/top.c
linux-3.8.13/tools/perf/util/top.h
linux-3.8.13/tools/perf/util/trace-event-info.c
linux-3.8.13/tools/perf/util/trace-event-parse.c
linux-3.8.13/tools/perf/util/trace-event-read.c
linux-3.8.13/tools/perf/util/trace-event-scripting.c
linux-3.8.13/tools/perf/util/trace-event.h
linux-3.8.13/tools/perf/util/types.h
linux-3.8.13/tools/perf/util/unwind.c
linux-3.8.13/tools/perf/util/unwind.h
linux-3.8.13/tools/perf/util/usage.c
linux-3.8.13/tools/perf/util/util.c
linux-3.8.13/tools/perf/util/util.h
linux-3.8.13/tools/perf/util/values.c
linux-3.8.13/tools/perf/util/values.h
linux-3.8.13/tools/perf/util/vdso.c
linux-3.8.13/tools/perf/util/vdso.h
linux-3.8.13/tools/perf/util/wrapper.c
linux-3.8.13/tools/perf/util/xyarray.c
linux-3.8.13/tools/perf/util/xyarray.h
linux-3.8.13/tools/power/
linux-3.8.13/tools/power/acpi/
linux-3.8.13/tools/power/acpi/Makefile
linux-3.8.13/tools/power/acpi/acpidump.8
linux-3.8.13/tools/power/acpi/acpidump.c
linux-3.8.13/tools/power/cpupower/
linux-3.8.13/tools/power/cpupower/.gitignore
linux-3.8.13/tools/power/cpupower/Makefile
linux-3.8.13/tools/power/cpupower/README
linux-3.8.13/tools/power/cpupower/ToDo
linux-3.8.13/tools/power/cpupower/bench/
linux-3.8.13/tools/power/cpupower/bench/Makefile
linux-3.8.13/tools/power/cpupower/bench/README-BENCH
linux-3.8.13/tools/power/cpupower/bench/benchmark.c
linux-3.8.13/tools/power/cpupower/bench/benchmark.h
linux-3.8.13/tools/power/cpupower/bench/config.h
linux-3.8.13/tools/power/cpupower/bench/cpufreq-bench_plot.sh
linux-3.8.13/tools/power/cpupower/bench/cpufreq-bench_script.sh
linux-3.8.13/tools/power/cpupower/bench/example.cfg
linux-3.8.13/tools/power/cpupower/bench/main.c
linux-3.8.13/tools/power/cpupower/bench/parse.c
linux-3.8.13/tools/power/cpupower/bench/parse.h
linux-3.8.13/tools/power/cpupower/bench/system.c
linux-3.8.13/tools/power/cpupower/bench/system.h
linux-3.8.13/tools/power/cpupower/debug/
linux-3.8.13/tools/power/cpupower/debug/i386/
linux-3.8.13/tools/power/cpupower/debug/i386/Makefile
linux-3.8.13/tools/power/cpupower/debug/i386/centrino-decode.c
linux-3.8.13/tools/power/cpupower/debug/i386/dump_psb.c
linux-3.8.13/tools/power/cpupower/debug/i386/intel_gsic.c
linux-3.8.13/tools/power/cpupower/debug/i386/powernow-k8-decode.c
linux-3.8.13/tools/power/cpupower/debug/kernel/
linux-3.8.13/tools/power/cpupower/debug/kernel/Makefile
linux-3.8.13/tools/power/cpupower/debug/kernel/cpufreq-test_tsc.c
linux-3.8.13/tools/power/cpupower/debug/x86_64/
linux-3.8.13/tools/power/cpupower/debug/x86_64/Makefile
linux-3.8.13/tools/power/cpupower/lib/
linux-3.8.13/tools/power/cpupower/lib/cpufreq.c
linux-3.8.13/tools/power/cpupower/lib/cpufreq.h
linux-3.8.13/tools/power/cpupower/lib/sysfs.c
linux-3.8.13/tools/power/cpupower/lib/sysfs.h
linux-3.8.13/tools/power/cpupower/man/
linux-3.8.13/tools/power/cpupower/man/cpupower-frequency-info.1
linux-3.8.13/tools/power/cpupower/man/cpupower-frequency-set.1
linux-3.8.13/tools/power/cpupower/man/cpupower-idle-info.1
linux-3.8.13/tools/power/cpupower/man/cpupower-info.1
linux-3.8.13/tools/power/cpupower/man/cpupower-monitor.1
linux-3.8.13/tools/power/cpupower/man/cpupower-set.1
linux-3.8.13/tools/power/cpupower/man/cpupower.1
linux-3.8.13/tools/power/cpupower/po/
linux-3.8.13/tools/power/cpupower/po/cs.po
linux-3.8.13/tools/power/cpupower/po/de.po
linux-3.8.13/tools/power/cpupower/po/fr.po
linux-3.8.13/tools/power/cpupower/po/it.po
linux-3.8.13/tools/power/cpupower/po/pt.po
linux-3.8.13/tools/power/cpupower/utils/
linux-3.8.13/tools/power/cpupower/utils/builtin.h
linux-3.8.13/tools/power/cpupower/utils/cpufreq-info.c
linux-3.8.13/tools/power/cpupower/utils/cpufreq-set.c
linux-3.8.13/tools/power/cpupower/utils/cpuidle-info.c
linux-3.8.13/tools/power/cpupower/utils/cpupower-info.c
linux-3.8.13/tools/power/cpupower/utils/cpupower-set.c
linux-3.8.13/tools/power/cpupower/utils/cpupower.c
linux-3.8.13/tools/power/cpupower/utils/helpers/
linux-3.8.13/tools/power/cpupower/utils/helpers/amd.c
linux-3.8.13/tools/power/cpupower/utils/helpers/bitmask.c
linux-3.8.13/tools/power/cpupower/utils/helpers/bitmask.h
linux-3.8.13/tools/power/cpupower/utils/helpers/cpuid.c
linux-3.8.13/tools/power/cpupower/utils/helpers/helpers.h
linux-3.8.13/tools/power/cpupower/utils/helpers/misc.c
linux-3.8.13/tools/power/cpupower/utils/helpers/msr.c
linux-3.8.13/tools/power/cpupower/utils/helpers/pci.c
linux-3.8.13/tools/power/cpupower/utils/helpers/sysfs.c
linux-3.8.13/tools/power/cpupower/utils/helpers/sysfs.h
linux-3.8.13/tools/power/cpupower/utils/helpers/topology.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/amd_fam14h_idle.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/cpuidle_sysfs.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/cpupower-monitor.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/cpupower-monitor.h
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/idle_monitors.def
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/idle_monitors.h
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/mperf_monitor.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/nhm_idle.c
linux-3.8.13/tools/power/cpupower/utils/idle_monitor/snb_idle.c
linux-3.8.13/tools/power/cpupower/utils/version-gen.sh
linux-3.8.13/tools/power/x86/
linux-3.8.13/tools/power/x86/turbostat/
linux-3.8.13/tools/power/x86/turbostat/Makefile
linux-3.8.13/tools/power/x86/turbostat/turbostat.8
linux-3.8.13/tools/power/x86/turbostat/turbostat.c
linux-3.8.13/tools/power/x86/x86_energy_perf_policy/
linux-3.8.13/tools/power/x86/x86_energy_perf_policy/Makefile
linux-3.8.13/tools/power/x86/x86_energy_perf_policy/x86_energy_perf_policy.8
linux-3.8.13/tools/power/x86/x86_energy_perf_policy/x86_energy_perf_policy.c
linux-3.8.13/tools/scripts/
linux-3.8.13/tools/scripts/Makefile.include
linux-3.8.13/tools/testing/
linux-3.8.13/tools/testing/fault-injection/
linux-3.8.13/tools/testing/fault-injection/failcmd.sh
linux-3.8.13/tools/testing/ktest/
linux-3.8.13/tools/testing/ktest/compare-ktest-sample.pl
linux-3.8.13/tools/testing/ktest/examples/
linux-3.8.13/tools/testing/ktest/examples/README
linux-3.8.13/tools/testing/ktest/examples/crosstests.conf
linux-3.8.13/tools/testing/ktest/examples/include/
linux-3.8.13/tools/testing/ktest/examples/include/bisect.conf
linux-3.8.13/tools/testing/ktest/examples/include/defaults.conf
linux-3.8.13/tools/testing/ktest/examples/include/min-config.conf
linux-3.8.13/tools/testing/ktest/examples/include/patchcheck.conf
linux-3.8.13/tools/testing/ktest/examples/include/tests.conf
linux-3.8.13/tools/testing/ktest/examples/kvm.conf
linux-3.8.13/tools/testing/ktest/examples/snowball.conf
linux-3.8.13/tools/testing/ktest/examples/test.conf
linux-3.8.13/tools/testing/ktest/ktest.pl
linux-3.8.13/tools/testing/ktest/sample.conf
linux-3.8.13/tools/testing/selftests/
linux-3.8.13/tools/testing/selftests/Makefile
linux-3.8.13/tools/testing/selftests/breakpoints/
linux-3.8.13/tools/testing/selftests/breakpoints/Makefile
linux-3.8.13/tools/testing/selftests/breakpoints/breakpoint_test.c
linux-3.8.13/tools/testing/selftests/cpu-hotplug/
linux-3.8.13/tools/testing/selftests/cpu-hotplug/Makefile
linux-3.8.13/tools/testing/selftests/cpu-hotplug/on-off-test.sh
linux-3.8.13/tools/testing/selftests/ipc/
linux-3.8.13/tools/testing/selftests/ipc/Makefile
linux-3.8.13/tools/testing/selftests/ipc/msgque.c
linux-3.8.13/tools/testing/selftests/kcmp/
linux-3.8.13/tools/testing/selftests/kcmp/Makefile
linux-3.8.13/tools/testing/selftests/kcmp/kcmp_test.c
linux-3.8.13/tools/testing/selftests/memory-hotplug/
linux-3.8.13/tools/testing/selftests/memory-hotplug/Makefile
linux-3.8.13/tools/testing/selftests/memory-hotplug/on-off-test.sh
linux-3.8.13/tools/testing/selftests/mqueue/
linux-3.8.13/tools/testing/selftests/mqueue/.gitignore
linux-3.8.13/tools/testing/selftests/mqueue/Makefile
linux-3.8.13/tools/testing/selftests/mqueue/mq_open_tests.c
linux-3.8.13/tools/testing/selftests/mqueue/mq_perf_tests.c
linux-3.8.13/tools/testing/selftests/vm/
linux-3.8.13/tools/testing/selftests/vm/Makefile
linux-3.8.13/tools/testing/selftests/vm/hugepage-mmap.c
linux-3.8.13/tools/testing/selftests/vm/hugepage-shm.c
linux-3.8.13/tools/testing/selftests/vm/map_hugetlb.c
linux-3.8.13/tools/testing/selftests/vm/run_vmtests
linux-3.8.13/tools/testing/selftests/vm/thuge-gen.c
linux-3.8.13/tools/usb/
linux-3.8.13/tools/usb/Makefile
linux-3.8.13/tools/usb/ffs-test.c
linux-3.8.13/tools/usb/hcd-tests.sh
linux-3.8.13/tools/usb/testusb.c
linux-3.8.13/tools/virtio/
linux-3.8.13/tools/virtio/Makefile
linux-3.8.13/tools/virtio/linux/
linux-3.8.13/tools/virtio/linux/device.h
linux-3.8.13/tools/virtio/linux/hrtimer.h
linux-3.8.13/tools/virtio/linux/module.h
linux-3.8.13/tools/virtio/linux/slab.h
linux-3.8.13/tools/virtio/linux/virtio.h
linux-3.8.13/tools/virtio/vhost_test/
linux-3.8.13/tools/virtio/vhost_test/Makefile
linux-3.8.13/tools/virtio/vhost_test/vhost_test.c
linux-3.8.13/tools/virtio/virtio-trace/
linux-3.8.13/tools/virtio/virtio-trace/Makefile
linux-3.8.13/tools/virtio/virtio-trace/README
linux-3.8.13/tools/virtio/virtio-trace/trace-agent-ctl.c
linux-3.8.13/tools/virtio/virtio-trace/trace-agent-rw.c
linux-3.8.13/tools/virtio/virtio-trace/trace-agent.c
linux-3.8.13/tools/virtio/virtio-trace/trace-agent.h
linux-3.8.13/tools/virtio/virtio_test.c
linux-3.8.13/tools/vm/
linux-3.8.13/tools/vm/.gitignore
linux-3.8.13/tools/vm/Makefile
linux-3.8.13/tools/vm/page-types.c
linux-3.8.13/tools/vm/slabinfo.c
linux-3.8.13/usr/
linux-3.8.13/usr/.gitignore
linux-3.8.13/usr/Kconfig
linux-3.8.13/usr/Makefile
linux-3.8.13/usr/gen_init_cpio.c
linux-3.8.13/usr/initramfs_data.S
linux-3.8.13/virt/
linux-3.8.13/virt/kvm/
linux-3.8.13/virt/kvm/Kconfig
linux-3.8.13/virt/kvm/assigned-dev.c
linux-3.8.13/virt/kvm/async_pf.c
linux-3.8.13/virt/kvm/async_pf.h
linux-3.8.13/virt/kvm/coalesced_mmio.c
linux-3.8.13/virt/kvm/coalesced_mmio.h
linux-3.8.13/virt/kvm/eventfd.c
linux-3.8.13/virt/kvm/ioapic.c
linux-3.8.13/virt/kvm/ioapic.h
linux-3.8.13/virt/kvm/iodev.h
linux-3.8.13/virt/kvm/iommu.c
linux-3.8.13/virt/kvm/irq_comm.c
linux-3.8.13/virt/kvm/kvm_main.c
applying patch patch-3.8.13-bone63.diff.gz to linux-3.8.13...
patching file Documentation/ABI/testing/sysfs-bus-iio-mpu6050
patching file Documentation/ABI/testing/sysfs-class-pwm
patching file Documentation/devices.txt
patching file Documentation/devicetree/00-INDEX
patching file Documentation/devicetree/bindings/arm/omap/omap.txt
patching file Documentation/devicetree/bindings/bus/ti-gpmc.txt
patching file Documentation/devicetree/bindings/crypto/omap-aes.txt
patching file Documentation/devicetree/bindings/crypto/omap-sham.txt
patching file Documentation/devicetree/bindings/dma/dma.txt
patching file Documentation/devicetree/bindings/dma/ti-edma.txt
patching file Documentation/devicetree/bindings/drm/tilcdc/panel.txt
patching file Documentation/devicetree/bindings/drm/tilcdc/slave.txt
patching file Documentation/devicetree/bindings/drm/tilcdc/tfp410.txt
patching file Documentation/devicetree/bindings/drm/tilcdc/tilcdc.txt
patching file Documentation/devicetree/bindings/hwmon/am335x-bandgap.txt
patching file Documentation/devicetree/bindings/input/touchscreen/ti-tsc-adc.txt
patching file Documentation/devicetree/bindings/leds/leds-pwm.txt
patching file Documentation/devicetree/bindings/misc/capes-beaglebone.txt
patching file Documentation/devicetree/bindings/mmc/ti-omap-hsmmc.txt
patching file Documentation/devicetree/bindings/mtd/gpmc-nor.txt
patching file Documentation/devicetree/bindings/mtd/gpmc-onenand.txt
patching file Documentation/devicetree/bindings/net/cpsw.txt
patching file Documentation/devicetree/bindings/net/gpmc-eth.txt
patching file Documentation/devicetree/bindings/pps/pps-gpio.txt
patching file Documentation/devicetree/bindings/pwm/nxp,pca9685-pwm.txt
patching file Documentation/devicetree/bindings/rtc/rtc-omap.txt
patching file Documentation/devicetree/bindings/sound/davinci-evm-audio.txt
patching file Documentation/devicetree/bindings/spi/omap-spi.txt
patching file Documentation/devicetree/bindings/usb/omap-usb.txt
patching file Documentation/devicetree/bindings/usb/usb-phy.txt
patching file Documentation/devicetree/bindings/vendor-prefixes.txt
patching file Documentation/devicetree/bindings/video/backlight/pwm-backlight.tx                                                                                t
patching file Documentation/devicetree/bindings/video/display-timing.txt
patching file Documentation/devicetree/bindings/video/fb-da8xx.txt
patching file Documentation/devicetree/bindings/video/ssd1307fb.txt
patching file Documentation/devicetree/dt-object-internal.txt
patching file Documentation/devicetree/dynamic-resolution-notes.txt
patching file Documentation/devicetree/overlay-notes.txt
patching file Documentation/hwmon/htu21
patching file Documentation/pwm.txt
patching file Makefile
patching file arch/arm/Kconfig
patching file arch/arm/Makefile
patching file arch/arm/boot/Makefile
patching file arch/arm/boot/dts/Makefile
patching file arch/arm/boot/dts/am335x-bone-common.dtsi
patching file arch/arm/boot/dts/am335x-bone.dts
patching file arch/arm/boot/dts/am335x-boneblack.dts
patching file arch/arm/boot/dts/am335x-evm.dts
patching file arch/arm/boot/dts/am335x-evmsk.dts
patching file arch/arm/boot/dts/am335x-tester.dts
patching file arch/arm/boot/dts/am33xx.dtsi
patching file arch/arm/common/Kconfig
patching file arch/arm/common/Makefile
patching file arch/arm/common/edma.c
patching file arch/arm/configs/da8xx_omapl_defconfig
patching file arch/arm/configs/omap2plus_defconfig
patching file arch/arm/include/asm/irq.h
patching file arch/arm/kernel/setup.c
patching file arch/arm/lib/memset.S
patching file arch/arm/mach-davinci/Makefile
patching file arch/arm/mach-davinci/board-tnetv107x-evm.c
patching file arch/arm/mach-davinci/davinci.h
patching file arch/arm/mach-davinci/devices-tnetv107x.c
patching file arch/arm/mach-davinci/devices.c
patching file arch/arm/mach-davinci/dm355.c
patching file arch/arm/mach-davinci/dm365.c
patching file arch/arm/mach-davinci/dm644x.c
patching file arch/arm/mach-davinci/dm646x.c
patching file arch/arm/mach-davinci/dma.c
patching file arch/arm/mach-davinci/include/mach/da8xx.h
patching file arch/arm/mach-davinci/include/mach/edma.h
patching file arch/arm/mach-omap2/Kconfig
patching file arch/arm/mach-omap2/Makefile
patching file arch/arm/mach-omap2/am33xx-cpsw.c
patching file arch/arm/mach-omap2/am33xx-restart.c
patching file arch/arm/mach-omap2/board-2430sdp.c
patching file arch/arm/mach-omap2/board-3430sdp.c
patching file arch/arm/mach-omap2/board-4430sdp.c
patching file arch/arm/mach-omap2/board-cm-t35.c
patching file arch/arm/mach-omap2/board-devkit8000.c
patching file arch/arm/mach-omap2/board-generic.c
patching file arch/arm/mach-omap2/board-igep0020.c
patching file arch/arm/mach-omap2/board-ldp.c
patching file arch/arm/mach-omap2/board-omap3beagle.c
patching file arch/arm/mach-omap2/board-omap3evm.c
patching file arch/arm/mach-omap2/board-omap3logic.c
patching file arch/arm/mach-omap2/board-omap3pandora.c
patching file arch/arm/mach-omap2/board-omap3stalker.c
patching file arch/arm/mach-omap2/board-omap3touchbook.c
patching file arch/arm/mach-omap2/board-omap4panda.c
patching file arch/arm/mach-omap2/board-overo.c
patching file arch/arm/mach-omap2/board-rm680.c
patching file arch/arm/mach-omap2/board-zoom-peripherals.c
patching file arch/arm/mach-omap2/cclock2430_data.c
patching file arch/arm/mach-omap2/cclock33xx_data.c
patching file arch/arm/mach-omap2/cclock3xxx_data.c
patching file arch/arm/mach-omap2/clkt_dpll.c
patching file arch/arm/mach-omap2/clock.h
patching file arch/arm/mach-omap2/cm33xx.c
patching file arch/arm/mach-omap2/common.h
patching file arch/arm/mach-omap2/control.h
patching file arch/arm/mach-omap2/devices.c
patching file arch/arm/mach-omap2/dpll3xxx.c
patching file arch/arm/mach-omap2/gpmc-nand.c
patching file arch/arm/mach-omap2/gpmc-onenand.c
patching file arch/arm/mach-omap2/gpmc-smc91x.c
patching file arch/arm/mach-omap2/gpmc.c
patching file arch/arm/mach-omap2/gpmc.h
patching file arch/arm/mach-omap2/gpu.c
patching file arch/arm/mach-omap2/id.c
patching file arch/arm/mach-omap2/io.c
patching file arch/arm/mach-omap2/irq.c
patching file arch/arm/mach-omap2/omap_device.c
patching file arch/arm/mach-omap2/omap_hwmod.c
patching file arch/arm/mach-omap2/omap_hwmod_2420_data.c
patching file arch/arm/mach-omap2/omap_hwmod_2430_data.c
patching file arch/arm/mach-omap2/omap_hwmod_2xxx_interconnect_data.c
patching file arch/arm/mach-omap2/omap_hwmod_2xxx_ipblock_data.c
patching file arch/arm/mach-omap2/omap_hwmod_33xx_data.c
patching file arch/arm/mach-omap2/omap_hwmod_3xxx_data.c
patching file arch/arm/mach-omap2/omap_hwmod_44xx_data.c
patching file arch/arm/mach-omap2/omap_hwmod_common_data.h
patching file arch/arm/mach-omap2/soc.h
patching file arch/arm/mach-omap2/twl-common.c
patching file arch/arm/mach-omap2/twl-common.h
patching file arch/arm/mach-omap2/usb-musb.c
patching file arch/arm/mach-omap2/usb-tusb6010.c
patching file arch/arm/plat-omap/Kconfig
patching file defconfig
patching file drivers/Kconfig
patching file drivers/Makefile
patching file drivers/base/platform.c
patching file drivers/char/tpm/Kconfig
patching file drivers/char/tpm/Makefile
patching file drivers/char/tpm/tpm-interface.c
patching file drivers/char/tpm/tpm.c
patching file drivers/char/tpm/tpm.h
patching file drivers/char/tpm/tpm_acpi.c
patching file drivers/char/tpm/tpm_atmel.c
patching file drivers/char/tpm/tpm_eventlog.c
patching file drivers/char/tpm/tpm_i2c_atmel.c
patching file drivers/char/tpm/tpm_i2c_infineon.c
patching file drivers/char/tpm/tpm_ibmvtpm.c
patching file drivers/char/tpm/tpm_nsc.c
patching file drivers/char/tpm/tpm_ppi.c
patching file drivers/char/tpm/tpm_tis.c
patching file drivers/char/virtio_console.c
patching file drivers/clk/clk-divider.c
patching file drivers/clk/clk.c
patching file drivers/crypto/omap-aes.c
patching file drivers/crypto/omap-sham.c
patching file drivers/dma/Kconfig
patching file drivers/dma/dmaengine.c
patching file drivers/dma/edma.c
patching file drivers/gpio/Kconfig
patching file drivers/gpio/Makefile
patching file drivers/gpio/gpio-of-helper.c
patching file drivers/gpu/drm/Kconfig
patching file drivers/gpu/drm/Makefile
patching file drivers/gpu/drm/drm_encoder_slave.c
patching file drivers/gpu/drm/drm_fb_cma_helper.c
patching file drivers/gpu/drm/drm_gem_cma_helper.c
patching file drivers/gpu/drm/drm_irq.c
patching file drivers/gpu/drm/drm_modes.c
patching file drivers/gpu/drm/i2c/Kconfig
patching file drivers/gpu/drm/i2c/Makefile
patching file drivers/gpu/drm/i2c/tda998x_audio_drv.c
patching file drivers/gpu/drm/i2c/tda998x_drv.c
patching file drivers/gpu/drm/nouveau/Kconfig
patching file drivers/gpu/drm/nouveau/nv04_tv.c
patching file drivers/gpu/drm/tilcdc/Kconfig
patching file drivers/gpu/drm/tilcdc/Makefile
patching file drivers/gpu/drm/tilcdc/tilcdc_crtc.c
patching file drivers/gpu/drm/tilcdc/tilcdc_drv.c
patching file drivers/gpu/drm/tilcdc/tilcdc_drv.h
patching file drivers/gpu/drm/tilcdc/tilcdc_panel.c
patching file drivers/gpu/drm/tilcdc/tilcdc_panel.h
patching file drivers/gpu/drm/tilcdc/tilcdc_regs.h
patching file drivers/gpu/drm/tilcdc/tilcdc_slave.c
patching file drivers/gpu/drm/tilcdc/tilcdc_slave.h
patching file drivers/gpu/drm/tilcdc/tilcdc_tfp410.c
patching file drivers/gpu/drm/tilcdc/tilcdc_tfp410.h
patching file drivers/hwmon/Kconfig
patching file drivers/hwmon/Makefile
patching file drivers/hwmon/am335x-bandgap.c
patching file drivers/hwmon/htu21.c
patching file drivers/i2c/busses/i2c-omap.c
patching file drivers/i2c/muxes/i2c-mux-pca954x.c
patching file drivers/iio/accel/Kconfig
patching file drivers/iio/accel/Makefile
patching file drivers/iio/accel/st_accel.h
patching file drivers/iio/accel/st_accel_buffer.c
patching file drivers/iio/accel/st_accel_core.c
patching file drivers/iio/accel/st_accel_i2c.c
patching file drivers/iio/accel/st_accel_spi.c
patching file drivers/iio/adc/ti_am335x_adc.c
patching file drivers/iio/common/Kconfig
patching file drivers/iio/common/Makefile
patching file drivers/iio/common/st_sensors/Kconfig
patching file drivers/iio/common/st_sensors/Makefile
patching file drivers/iio/common/st_sensors/st_sensors_buffer.c
patching file drivers/iio/common/st_sensors/st_sensors_core.c
patching file drivers/iio/common/st_sensors/st_sensors_i2c.c
patching file drivers/iio/common/st_sensors/st_sensors_spi.c
patching file drivers/iio/common/st_sensors/st_sensors_trigger.c
patching file drivers/iio/gyro/Kconfig
patching file drivers/iio/gyro/Makefile
patching file drivers/iio/gyro/st_gyro.h
patching file drivers/iio/gyro/st_gyro_buffer.c
patching file drivers/iio/gyro/st_gyro_core.c
patching file drivers/iio/gyro/st_gyro_i2c.c
patching file drivers/iio/gyro/st_gyro_spi.c
patching file drivers/iio/imu/Kconfig
patching file drivers/iio/imu/Makefile
patching file drivers/iio/imu/inv_mpu6050/Kconfig
patching file drivers/iio/imu/inv_mpu6050/Makefile
patching file drivers/iio/imu/inv_mpu6050/inv_mpu_core.c
patching file drivers/iio/imu/inv_mpu6050/inv_mpu_iio.h
patching file drivers/iio/imu/inv_mpu6050/inv_mpu_ring.c
patching file drivers/iio/imu/inv_mpu6050/inv_mpu_trigger.c
patching file drivers/iio/magnetometer/Kconfig
patching file drivers/iio/magnetometer/Makefile
patching file drivers/iio/magnetometer/st_magn.h
patching file drivers/iio/magnetometer/st_magn_buffer.c
patching file drivers/iio/magnetometer/st_magn_core.c
patching file drivers/iio/magnetometer/st_magn_i2c.c
patching file drivers/iio/magnetometer/st_magn_spi.c
patching file drivers/input/keyboard/gpio_keys.c
patching file drivers/input/touchscreen/atmel_mxt_ts.c
patching file drivers/input/touchscreen/ti_am335x_tsc.c
patching file drivers/leds/Kconfig
patching file drivers/leds/leds-pwm.c
patching file drivers/media/i2c/soc_camera/Kconfig
patching file drivers/media/i2c/soc_camera/Makefile
patching file drivers/media/i2c/soc_camera/mt9m114.c
patching file drivers/media/i2c/soc_camera/mt9t112.c
patching file drivers/media/platform/soc_camera/Kconfig
patching file drivers/media/platform/soc_camera/Makefile
patching file drivers/media/platform/soc_camera/cssp_camera.c
patching file drivers/media/usb/uvc/uvc_ctrl.c
patching file drivers/mfd/omap-usb-host.c
patching file drivers/mfd/ti_am335x_tscadc.c
patching file drivers/mfd/tps65217.c
patching file drivers/misc/Kconfig
patching file drivers/misc/Makefile
patching file drivers/misc/cape/Kconfig
patching file drivers/misc/cape/Makefile
patching file drivers/misc/cape/beaglebone/Kconfig
patching file drivers/misc/cape/beaglebone/Makefile
patching file drivers/misc/cape/beaglebone/bone-iio-helper.c
patching file drivers/misc/cape/beaglebone/bone-pinmux-helper.c
patching file drivers/misc/cape/beaglebone/cape-bone-argus.c
patching file drivers/misc/cape/beaglebone/cape-bone-geiger.c
patching file drivers/misc/cape/beaglebone/cape-bone-nixie.c
patching file drivers/misc/cape/beaglebone/capemgr.c
patching file drivers/misc/cape/beaglebone/logibone/Kconfig
patching file drivers/misc/cape/beaglebone/logibone/Makefile
patching file drivers/misc/cape/beaglebone/logibone/drvr.h
patching file drivers/misc/cape/beaglebone/logibone/generic.h
patching file drivers/misc/cape/beaglebone/logibone/ioctl.c
patching file drivers/misc/cape/beaglebone/logibone/ioctl.h
patching file drivers/misc/cape/beaglebone/logibone/main_dma.c
patching file drivers/misc/eeprom/at24.c
patching file drivers/misc/gpevt.c
patching file drivers/misc/grove-i2c.c
patching file drivers/misc/ti-st/st_kim.c
patching file drivers/misc/tieqep.c
patching file drivers/misc/tsl2550.c
patching file drivers/mmc/host/Kconfig
patching file drivers/mmc/host/davinci_mmc.c
patching file drivers/mmc/host/omap_hsmmc.c
patching file drivers/mtd/nand/omap2.c
patching file drivers/mtd/onenand/omap2.c
patching file drivers/net/can/mcp251x.c
patching file drivers/net/ethernet/smsc/smsc911x.c
patching file drivers/net/ethernet/ti/cpsw.c
patching file drivers/net/ethernet/ti/davinci_cpdma.c
patching file drivers/net/ethernet/ti/davinci_cpdma.h
patching file drivers/net/ethernet/ti/davinci_mdio.c
patching file drivers/net/ieee802154/mrf24j40.c
patching file drivers/net/wireless/Kconfig
patching file drivers/net/wireless/Makefile
patching file drivers/net/wireless/rtl8192cu/Kconfig
patching file drivers/net/wireless/rtl8192cu/Makefile
patching file drivers/net/wireless/rtl8192cu/clean
patching file drivers/net/wireless/rtl8192cu/core/efuse/rtw_efuse.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_ap.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_br_ext.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_cmd.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_debug.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_eeprom.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_ieee80211.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_io.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_ioctl_query.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_ioctl_rtl.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_ioctl_set.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_iol.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_mlme.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_mlme_ext.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_mp.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_mp_ioctl.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_p2p.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_pwrctrl.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_recv.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_rf.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_security.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_sreset.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_sta_mgt.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_tdls.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_wlan_util.c
patching file drivers/net/wireless/rtl8192cu/core/rtw_xmit.c
patching file drivers/net/wireless/rtl8192cu/hal/HalPwrSeqCmd.c
patching file drivers/net/wireless/rtl8192cu/hal/dm.c
patching file drivers/net/wireless/rtl8192cu/hal/dm.h
patching file drivers/net/wireless/rtl8192cu/hal/hal_com.c
patching file drivers/net/wireless/rtl8192cu/hal/hal_intf.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_cmd.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_dm.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_hal_init.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_mp.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_phycfg.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_rf6052.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_rxdesc.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_sreset.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/rtl8192c_xmit.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/Hal8192CUHWImg.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/Hal8192CUHWImg_wow                                                                                lan.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/rtl8192cu_led.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/rtl8192cu_recv.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/rtl8192cu_xmit.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/usb_halinit.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/usb_ops_ce.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/usb_ops_linux.c
patching file drivers/net/wireless/rtl8192cu/hal/rtl8192c/usb/usb_ops_xp.c
patching file drivers/net/wireless/rtl8192cu/ifcfg-wlan0
patching file drivers/net/wireless/rtl8192cu/include/Hal8192CEHWImg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192CPhyCfg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192CPhyReg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192CUHWImg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192CUHWImg_wowlan.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192DEHWImg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192DPhyCfg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192DPhyReg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192DUHWImg.h
patching file drivers/net/wireless/rtl8192cu/include/Hal8192DUHWImg_wowlan.h
patching file drivers/net/wireless/rtl8192cu/include/HalPwrSeqCmd.h
patching file drivers/net/wireless/rtl8192cu/include/autoconf.h
patching file drivers/net/wireless/rtl8192cu/include/basic_types.h
patching file drivers/net/wireless/rtl8192cu/include/byteorder/big_endian.h
patching file drivers/net/wireless/rtl8192cu/include/byteorder/generic.h
patching file drivers/net/wireless/rtl8192cu/include/byteorder/little_endian.h
patching file drivers/net/wireless/rtl8192cu/include/byteorder/swab.h
patching file drivers/net/wireless/rtl8192cu/include/byteorder/swabb.h
patching file drivers/net/wireless/rtl8192cu/include/circ_buf.h
patching file drivers/net/wireless/rtl8192cu/include/cmd_osdep.h
patching file drivers/net/wireless/rtl8192cu/include/drv_conf.h
patching file drivers/net/wireless/rtl8192cu/include/drv_types.h
patching file drivers/net/wireless/rtl8192cu/include/drv_types_ce.h
patching file drivers/net/wireless/rtl8192cu/include/drv_types_linux.h
patching file drivers/net/wireless/rtl8192cu/include/drv_types_sdio.h
patching file drivers/net/wireless/rtl8192cu/include/drv_types_xp.h
patching file drivers/net/wireless/rtl8192cu/include/ethernet.h
patching file drivers/net/wireless/rtl8192cu/include/h2clbk.h
patching file drivers/net/wireless/rtl8192cu/include/hal_com.h
patching file drivers/net/wireless/rtl8192cu/include/hal_intf.h
patching file drivers/net/wireless/rtl8192cu/include/ieee80211.h
patching file drivers/net/wireless/rtl8192cu/include/ieee80211_ext.h
patching file drivers/net/wireless/rtl8192cu/include/if_ether.h
patching file drivers/net/wireless/rtl8192cu/include/ioctl_cfg80211.h
patching file drivers/net/wireless/rtl8192cu/include/ip.h
patching file drivers/net/wireless/rtl8192cu/include/linux/wireless.h
patching file drivers/net/wireless/rtl8192cu/include/mlme_osdep.h
patching file drivers/net/wireless/rtl8192cu/include/mp_custom_oid.h
patching file drivers/net/wireless/rtl8192cu/include/nic_spec.h
patching file drivers/net/wireless/rtl8192cu/include/osdep_ce_service.h
patching file drivers/net/wireless/rtl8192cu/include/osdep_intf.h
patching file drivers/net/wireless/rtl8192cu/include/osdep_service.h
patching file drivers/net/wireless/rtl8192cu/include/pci_hal.h
patching file drivers/net/wireless/rtl8192cu/include/pci_ops.h
patching file drivers/net/wireless/rtl8192cu/include/pci_osintf.h
patching file drivers/net/wireless/rtl8192cu/include/recv_osdep.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_cmd.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_dm.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_event.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_hal.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_led.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_recv.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_rf.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_spec.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_sreset.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192c_xmit.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_cmd.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_dm.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_hal.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_led.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_recv.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_rf.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_spec.h
patching file drivers/net/wireless/rtl8192cu/include/rtl8192d_xmit.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_android.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ap.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_br_ext.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_byteorder.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_cmd.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_debug.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_eeprom.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_efuse.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_event.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ht.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_io.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ioctl.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ioctl_query.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ioctl_rtl.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_ioctl_set.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_iol.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_led.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_mlme.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_mlme_ext.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_mp.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_mp_ioctl.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_mp_phy_regdef.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_p2p.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_pwrctrl.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_qos.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_recv.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_rf.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_security.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_sreset.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_tdls.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_version.h
patching file drivers/net/wireless/rtl8192cu/include/rtw_xmit.h
patching file drivers/net/wireless/rtl8192cu/include/sta_info.h
patching file drivers/net/wireless/rtl8192cu/include/usb_hal.h
patching file drivers/net/wireless/rtl8192cu/include/usb_ops.h
patching file drivers/net/wireless/rtl8192cu/include/usb_ops_linux.h
patching file drivers/net/wireless/rtl8192cu/include/usb_osintf.h
patching file drivers/net/wireless/rtl8192cu/include/usb_vendor_req.h
patching file drivers/net/wireless/rtl8192cu/include/wifi.h
patching file drivers/net/wireless/rtl8192cu/include/wlan_bssdef.h
patching file drivers/net/wireless/rtl8192cu/include/xmit_osdep.h
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/ioctl_cfg80211.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/ioctl_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/mlme_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/os_intfs.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/pci_intf.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/pci_ops_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/recv_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/rtw_android.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/usb_intf.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/usb_ops_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/linux/xmit_linux.c
patching file drivers/net/wireless/rtl8192cu/os_dep/osdep_service.c
patching file drivers/net/wireless/rtl8192cu/runwpa
patching file drivers/net/wireless/rtl8192cu/wlan0dhcp
patching file drivers/of/Kconfig
patching file drivers/of/Makefile
patching file drivers/of/base.c
patching file drivers/of/device.c
patching file drivers/of/dma.c
patching file drivers/of/of_i2c.c
patching file drivers/of/overlay.c
patching file drivers/of/resolver.c
patching file drivers/of/util.c
patching file drivers/pinctrl/pinctrl-single.c
patching file drivers/pps/clients/pps-gpio.c
patching file drivers/pwm/Kconfig
patching file drivers/pwm/Makefile
patching file drivers/pwm/core.c
patching file drivers/pwm/pwm-atmel-tcb.c
patching file drivers/pwm/pwm-bfin.c
patching file drivers/pwm/pwm-imx.c
patching file drivers/pwm/pwm-lpc32xx.c
patching file drivers/pwm/pwm-mxs.c
patching file drivers/pwm/pwm-pca9685.c
patching file drivers/pwm/pwm-puv3.c
patching file drivers/pwm/pwm-spear.c
patching file drivers/pwm/pwm-tegra.c
patching file drivers/pwm/pwm-tiehrpwm.c
patching file drivers/pwm/pwm_test.c
patching file drivers/regulator/core.c
patching file drivers/remoteproc/Kconfig
patching file drivers/remoteproc/Makefile
patching file drivers/remoteproc/beaglelogic.c
patching file drivers/remoteproc/beaglelogic.h
patching file drivers/remoteproc/beaglelogic_glue.h
patching file drivers/remoteproc/pru_rproc.c
patching file drivers/remoteproc/remoteproc_core.c
patching file drivers/rpmsg/Kconfig
patching file drivers/rpmsg/virtio_rpmsg_bus.c
patching file drivers/rstctl/Kconfig
patching file drivers/rstctl/Makefile
patching file drivers/rstctl/core.c
patching file drivers/rstctl/rstctl-gpio.c
patching file drivers/rstctl/rstctl-test-consumer.c
patching file drivers/rstctl/rstctl-test.c
patching file drivers/rtc/rtc-omap.c
patching file drivers/spi/spi-omap2-mcspi.c
patching file drivers/tty/Kconfig
patching file drivers/tty/Makefile
patching file drivers/tty/jhd629-i2c.c
patching file drivers/tty/serial/omap-serial.c
patching file drivers/uio/Kconfig
patching file drivers/uio/uio_pruss.c
patching file drivers/usb/core/hub.c
patching file drivers/usb/musb/Kconfig
patching file drivers/usb/musb/musb_core.c
patching file drivers/usb/musb/musb_dsps.c
patching file drivers/usb/musb/musb_host.c
patching file drivers/usb/musb/omap2430.c
patching file drivers/usb/musb/omap2430.h
patching file drivers/usb/otg/otg.c
patching file drivers/usb/otg/twl4030-usb.c
patching file drivers/usb/phy/Kconfig
patching file drivers/usb/phy/Makefile
patching file drivers/usb/phy/omap-control-usb.c
patching file drivers/usb/phy/omap-usb2.c
patching file drivers/vhost/test.c
patching file drivers/video/Kconfig
patching file drivers/video/Makefile
patching file drivers/video/backlight/Kconfig
patching file drivers/video/backlight/Makefile
patching file drivers/video/backlight/pwm_bl.c
patching file drivers/video/backlight/tlc59108.c
patching file drivers/video/backlight/tps65217_bl.c
patching file drivers/video/da8xx-fb.c
patching file drivers/video/display_timing.c
patching file drivers/video/fbmon.c
patching file drivers/video/hdmi.c
patching file drivers/video/modedb.c
patching file drivers/video/of_display_timing.c
patching file drivers/video/of_videomode.c
patching file drivers/video/omap2/displays/panel-generic-dpi.c
patching file drivers/video/omap2/dss/venc.c
patching file drivers/video/omap2/omapfb/omapfb-main.c
patching file drivers/video/ssd1307fb.c
patching file drivers/video/st7735fb.c
patching file drivers/video/st7735fb.h
patching file drivers/video/via/hw.c
patching file drivers/video/via/hw.h
patching file drivers/video/via/lcd.c
patching file drivers/video/via/share.h
patching file drivers/video/via/via_modesetting.c
patching file drivers/video/via/via_modesetting.h
patching file drivers/video/videomode.c
patching file drivers/virtio/virtio_ring.c
patching file drivers/w1/masters/w1-gpio.c
patching file firmware/.gitignore
patching file firmware/Makefile
File firmware/am335x-pm-firmware.bin: git binary diffs are not supported.
patching file firmware/capes/BB-ADC-00A0.dts
patching file firmware/capes/BB-BEAGLELOGIC-00A0.dts
patching file firmware/capes/BB-BONE-AUDI-01-00A0.dts
patching file firmware/capes/BB-BONE-AUDI-02-00A0.dts
patching file firmware/capes/BB-BONE-BACON-00A0.dts
patching file firmware/capes/BB-BONE-BACONE-00A0.dts
patching file firmware/capes/BB-BONE-BACONE2-00A0.dts
patching file firmware/capes/BB-BONE-CAM-VVDN-00A0.dts
patching file firmware/capes/BB-BONE-CAM3-01-00A2.dts
patching file firmware/capes/BB-BONE-CRYPTO-00A0.dts
patching file firmware/capes/BB-BONE-GPEVT-00A0.dts
patching file firmware/capes/BB-BONE-GPS-00A0.dts
patching file firmware/capes/BB-BONE-HAS-00R1.dts
patching file firmware/capes/BB-BONE-LCD4-01-00A0.dts
patching file firmware/capes/BB-BONE-LCD4-01-00A1.dts
patching file firmware/capes/BB-BONE-LCD7-01-00A2.dts
patching file firmware/capes/BB-BONE-LCD7-01-00A3.dts
patching file firmware/capes/BB-BONE-LCD7-01-00A4.dts
patching file firmware/capes/BB-BONE-LOGIBONE-00R1.dts
patching file firmware/capes/BB-BONE-PRU-01-00A0.dts
patching file firmware/capes/BB-BONE-PRU-02-00A0.dts
patching file firmware/capes/BB-BONE-PRU-03-00A0.dts
patching file firmware/capes/BB-BONE-PRU-04-00A0.dts
patching file firmware/capes/BB-BONE-PWMT-00A0.dts
patching file firmware/capes/BB-BONE-REPLICAP-00A1.dts
patching file firmware/capes/BB-BONE-REPLICAP-00A2.dts
patching file firmware/capes/BB-BONE-REPLICAP-00A3.dts
patching file firmware/capes/BB-BONE-REPLICAP-00A4.dts
patching file firmware/capes/BB-BONE-REPLICAP-0A4A.dts
patching file firmware/capes/BB-BONE-RS232-00A0.dts
patching file firmware/capes/BB-BONE-RST-00A0.dts
patching file firmware/capes/BB-BONE-RST2-00A0.dts
patching file firmware/capes/BB-BONE-RTC-00A0.dts
patching file firmware/capes/BB-BONE-SERL-01-00A1.dts
patching file firmware/capes/BB-BONE-SERL-01-00A2.dts
patching file firmware/capes/BB-BONE-SERL-03-00A1.dts
patching file firmware/capes/BB-BONE-eMMC1-01-00A0.dts
patching file firmware/capes/BB-BONELT-BT-00A0.dts
patching file firmware/capes/BB-GPIOHELP-00A0.dts
patching file firmware/capes/BB-I2C1-00A0.dts
patching file firmware/capes/BB-I2C1A1-00A0.dts
patching file firmware/capes/BB-SPIDEV0-00A0.dts
patching file firmware/capes/BB-SPIDEV1-00A0.dts
patching file firmware/capes/BB-SPIDEV1A1-00A0.dts
patching file firmware/capes/BB-UART1-00A0.dts
patching file firmware/capes/BB-UART2-00A0.dts
patching file firmware/capes/BB-UART2-RTSCTS-00A0.dts
patching file firmware/capes/BB-UART4-00A0.dts
patching file firmware/capes/BB-UART4-RTSCTS-00A0.dts
patching file firmware/capes/BB-UART5-00A0.dts
patching file firmware/capes/CBB-Relay-00A0.dts
patching file firmware/capes/DNIL-AMPCAPE-1-00R1.dts
patching file firmware/capes/TT3201-001-01.dts
patching file firmware/capes/am33xx_pwm-00A0.dts
patching file firmware/capes/bone_eqep0-00A0.dts
patching file firmware/capes/bone_eqep1-00A0.dts
patching file firmware/capes/bone_eqep2-00A0.dts
patching file firmware/capes/bone_pwm_P8_13-00A0.dts
patching file firmware/capes/bone_pwm_P8_19-00A0.dts
patching file firmware/capes/bone_pwm_P8_34-00A0.dts
patching file firmware/capes/bone_pwm_P8_36-00A0.dts
patching file firmware/capes/bone_pwm_P8_45-00A0.dts
patching file firmware/capes/bone_pwm_P8_46-00A0.dts
patching file firmware/capes/bone_pwm_P9_14-00A0.dts
patching file firmware/capes/bone_pwm_P9_16-00A0.dts
patching file firmware/capes/bone_pwm_P9_21-00A0.dts
patching file firmware/capes/bone_pwm_P9_22-00A0.dts
patching file firmware/capes/bone_pwm_P9_28-00A0.dts
patching file firmware/capes/bone_pwm_P9_29-00A0.dts
patching file firmware/capes/bone_pwm_P9_31-00A0.dts
patching file firmware/capes/bone_pwm_P9_42-00A0.dts
patching file firmware/capes/cape-CBB-Serial-r01.dts
patching file firmware/capes/cape-bebopr-R2.dts
patching file firmware/capes/cape-bebopr-brdg-R2.dts
patching file firmware/capes/cape-bebopr-ena-R2.dts
patching file firmware/capes/cape-bone-2g-emmc1.dts
patching file firmware/capes/cape-bone-adafruit-lcd-00A0.dts
patching file firmware/capes/cape-bone-argus-00A0.dts
patching file firmware/capes/cape-bone-dvi-00A0.dts
patching file firmware/capes/cape-bone-dvi-00A1.dts
patching file firmware/capes/cape-bone-dvi-00A2.dts
patching file firmware/capes/cape-bone-exptest-00A0.dts
patching file firmware/capes/cape-bone-geiger-00A0.dts
patching file firmware/capes/cape-bone-hexy-00A0.dts
patching file firmware/capes/cape-bone-ibb-00A0.dts
patching file firmware/capes/cape-bone-iio-00A0.dts
patching file firmware/capes/cape-bone-lcd3-00A0.dts
patching file firmware/capes/cape-bone-lcd3-00A2.dts
patching file firmware/capes/cape-bone-mrf24j40-00A0.dts
patching file firmware/capes/cape-bone-nixie-00A0.dts
patching file firmware/capes/cape-bone-pinmux-test-00A0.dts
patching file firmware/capes/cape-bone-proto-00A0.dts
patching file firmware/capes/cape-bone-tester-00A0.dts
patching file firmware/capes/cape-bone-weather-00A0.dts
patching file firmware/capes/cape-bone-weather-00B0.dts
patching file firmware/capes/cape-boneblack-hdmi-00A0.dts
patching file firmware/capes/cape-boneblack-hdmin-00A0.dts
patching file firmware/capes/cape-univ-emmc-00A0.dts
patching file firmware/capes/cape-universal-00A0.dts
patching file firmware/capes/cape-universaln-00A0.dts
patching file fs/fs-writeback.c
patching file include/drm/drmP.h
patching file include/drm/drm_encoder_slave.h
patching file include/drm/drm_fb_cma_helper.h
patching file include/drm/drm_gem_cma_helper.h
patching file include/drm/i2c/tda998x.h
patching file include/linux/can/platform/mcp251x.h
patching file include/linux/clk-private.h
patching file include/linux/clk-provider.h
patching file include/linux/dmaengine.h
patching file include/linux/fb.h
patching file include/linux/hdmi.h
patching file include/linux/i2c/eeprom.h
patching file include/linux/iio/common/st_sensors.h
patching file include/linux/iio/common/st_sensors_i2c.h
patching file include/linux/iio/common/st_sensors_spi.h
patching file include/linux/input/ti_am335x_tsc.h
patching file include/linux/leds_pwm.h
patching file include/linux/mfd/davinci_voicecodec.h
patching file include/linux/mfd/ti_am335x_tscadc.h
patching file include/linux/mfd/tps65217.h
patching file include/linux/of.h
patching file include/linux/of_dma.h
patching file include/linux/of_i2c.h
patching file include/linux/platform_data/cpsw.h
patching file include/linux/platform_data/edma.h
patching file include/linux/platform_data/invensense_mpu6050.h
patching file include/linux/platform_data/mmc-davinci.h
patching file include/linux/platform_data/mmc-omap.h
patching file include/linux/platform_data/mtd-nand-omap2.h
patching file include/linux/platform_data/mtd-onenand-omap2.h
patching file include/linux/platform_data/spi-davinci.h
patching file include/linux/platform_device.h
patching file include/linux/pwm.h
patching file include/linux/remoteproc.h
patching file include/linux/rstctl.h
patching file include/linux/tpm.h
patching file include/linux/usb/musb.h
patching file include/linux/usb/omap_control_usb.h
patching file include/linux/usb/omap_usb.h
patching file include/linux/usb/phy.h
patching file include/linux/writeback.h
patching file include/media/mt9t112.h
patching file include/media/v4l2-chip-ident.h
patching file include/uapi/linux/serial.h
patching file include/uapi/linux/serial_core.h
patching file include/video/display_timing.h
patching file include/video/of_display_timing.h
patching file include/video/of_videomode.h
patching file include/video/videomode.h
patching file kernel/printk.c
patching file net/ieee802154/6lowpan.c
patching file net/ieee802154/6lowpan.h
patching file net/mac802154/mac802154.h
patching file net/mac802154/mac_cmd.c
patching file net/mac802154/mib.c
patching file net/mac802154/wpan.c
patching file net/wireless/db.txt
patching file scripts/Makefile.lib
patching file scripts/dtc/checks.c
patching file scripts/dtc/dtc-lexer.l
patching file scripts/dtc/dtc-lexer.lex.c_shipped
patching file scripts/dtc/dtc-parser.tab.c_shipped
patching file scripts/dtc/dtc-parser.tab.h_shipped
patching file scripts/dtc/dtc-parser.y
patching file scripts/dtc/dtc.c
patching file scripts/dtc/dtc.h
patching file scripts/dtc/fdtdump.c
patching file scripts/dtc/flattree.c
patching file scripts/dtc/util.c
patching file scripts/package/builddeb
patching file sound/soc/davinci/Kconfig
patching file sound/soc/davinci/Makefile
patching file sound/soc/davinci/davinci-evm.c
patching file sound/soc/davinci/davinci-mcasp.c
patching file sound/soc/davinci/davinci-pcm.c
patching file sound/soc/davinci/davinci-pcm.h
patching file sound/soc/davinci/davinci-sffsdr.c
patching file tools/virtio/Makefile
patching file tools/virtio/linux/virtio.h
patching file tools/virtio/virtio_test.c
moving kernel source to /usr/src/linux-3.8.13-bone63...
preparing kernel source at /usr/src/linux-3.8.13-bone63...
  HOSTCC  scripts/basic/fixdep
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_e                                                                                lf12_bigarm_vgc
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
  HOSTCC  scripts/basic/fixdep
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_e                                                                                lf12_bigarm_vgc
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/                                                                                config/kernel.release'.  Stop.
  HOSTCC  scripts/basic/fixdep
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_e                                                                                lf12_bigarm_vgc
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
  HOSTCC  scripts/basic/fixdep
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_e                                                                                lf12_bigarm_vgc
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
done: kernel sources for 3.8.13-bone63 are now installed.
you should be able to compile kernel modules.


```
I do below command to compile kernel but occurred some errors.
```
root@arm:/usr/src/linux-3.8.13-bone63# make prepare
  HOSTCC  scripts/basic/fixdep
as: symbol lookup error: /usr/lib/libbfd-2.24-system.so: undefined symbol: bfd_elf12_bigarm_vgc
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
root@arm:/usr/src/linux-3.8.13-bone63#


```
Please help me to solve it.
Thanks you!

---

### Post by Doug S on 2014-10-08
Even the smallest of patch files (and this one is big) can be temperamental.
Are you certain that you have exactly the correct source kernel and exactly the correct patch set file for that kernel?
It seems you are using version 63 of the patch set, but I observe a version 64, 65, 66, and 67 also. ([Reference]("https://rcn-ee.net/deb/wheezy-armhf/") (which I do not know if it is actually a correct or relevant reference))

---

