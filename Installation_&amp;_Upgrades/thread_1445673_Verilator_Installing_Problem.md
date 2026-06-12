---
title: "Verilator Installing Problem"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by partihv2eng on 2010-04-02
Hi..I am trying to install Varilator (Verilog simulator) I am getting this kind of error msg

```
le test_sp/Makefile_obj  ; do \
      /usr/bin/install -c $p /usr/local/share/verilator/examples/$p; \
    done
/usr/bin/install: cannot stat `test_sp/*.[chv]*': No such file or directory
Installed!

Add to your startup file (for bash or csh, as appropriate):
    export VERILATOR_ROOT=/home/parthiv/Desktop/verilator-3.801
    setenv VERILATOR_ROOT /home/parthiv/Desktop/verilator-3.801  ; export VERILATOR_ROOT 

See 'verilator.txt' for documentation.
```

---

### Post by loose222 on 2010-08-10
Cycle accurate models in C and SystemC are becoming an increasingly       important part of the verification process, particularly for SoCs with       performance critical embedded software. They represent a software       friendly compromise, offering higher performance than traditional       event-driven simulation, but greater accuracy than hand-written       instruction set simulators (ISS) and transaction level models (TLM).     
       Typically such models follow 2-state, zero-delay synthesis semantics,       offering an early insight into the behavior of the synthesized       design. Applications include:     

[LIST]
[*]           Detailed performance analysis of systems, based on the actual           hardware implementation running with its embedded software. 	
[*]           Implementation of low level firmware, such as board support packages 	  codecs and specialist device drivers, which rely on exact behavior 	  of SoC peripherals. 	
[*] 	  Software optimization. This can be particularly important for codec 	  development, where the performance depends critically on interaction 	  between processor, memory, cache and MMU. In such scenarios, 	  estimates by ISS and TLM can be out by a factor of 3, resulting 	  either in wasted silicon, or chips that cannot meet their required 	  performance. 	
[/LIST]


=============
[house and land packages Melbourne](http://www.**********.com.au/)
[short sale assintance](http://www.***********.com)

---

