---
title: "samsung chromebook 2 upgrade xenial to yakkety, no sound or chrome keys"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by tribble43 on 2016-10-09
I'm running a samsung chromebook 2 (codename winky) w/ SeaBIOS.  I just installed Xubuntu a week or two ago.
Everything was working great with xenial (v16.04), even the chromekeys.  I upgraded to yakkety (v16.10) and the sound stopped working along with my chromekeys.
The chromekeys aren't absolutely essential to me, but the sound card is, so I started investigating.

It was the kernel upgrade from 4.4.0-38 to 4.8.0-19 that did it.  I tracked it down to a change in the kernel.  The driver for my soundcard is byt_max98090.
This is from the linux v4.8.0 file "sound/soc/intel/Kconfig":
------------------------------------------
config SND_SOC_INTEL_BYT_MAX98090_MACH
	tristate "ASoC Audio driver for Intel Baytrail with MAX98090 codec"
	depends on X86_INTEL_LPSS && I2C
	depends on DW_DMAC_CORE && (SND_SST_IPC_ACPI = n)
	select SND_SOC_INTEL_SST
	select SND_SOC_INTEL_SST_FIRMWARE
	select SND_SOC_INTEL_BAYTRAIL
	select SND_SOC_MAX98090
	help
	  This adds audio driver for Intel Baytrail platform based boards
	  with the MAX98090 audio codec.
------------------------------------------

notice above it says SND_SST_IPC_ACPI must be disabled, however the following drivers depend on that option being enabled:

SND_SOC_INTEL_BYTCR_RT5640_MACH
SND_SOC_INTEL_BYTCR_RT5651_MACH
SND_SOC_INTEL_CHT_BSW_RT5672_MACH
SND_SOC_INTEL_CHT_BSW_RT5645_MACH
SND_SOC_INTEL_CHT_BSW_MAX98090_TI_MACH

If those are enabled, the driver won't even appear in the 'menuconfig' display.
This is the commit which added the SND_SST_IPC_ACPI=n requirement to SND_SOC_INTEL_BYT_MAX98090_MACH:

[https://github.com/torvalds/linux/commit/cfffcc66a89ab6d9961b2cde6cdab2ba056451ad#diff-96c675eef8f66bed2bc1bdb772282f46](https://github.com/torvalds/linux/commit/cfffcc66a89ab6d9961b2cde6cdab2ba056451ad#diff-96c675eef8f66bed2bc1bdb772282f46)
-------------------------------------------------------------------
 ASoC: Intel: Load the atom DPCM driver only

DPCM driver is recommended for BYT, CHT based platforms, so if
CONFIG_SND_SST_IPC_ACPI is selected then don't compile the BYT
Device IDs in common ACPI driver to avoid probe conflicts.

Signed-off-by: Pierre-Louis Bossart <pierre-louis.bossart@linux.intel.com>
Acked-by: Jie Yang <yang.jie@intel.com>
Signed-off-by: Vinod Koul <vinod.koul@intel.com>
Signed-off-by: Mark Brown <broonie@kernel.org>
-------------------------------------------------------------------

So for now I'm just going to roll out my own ubuntu kernel with those drivers disabled, but I figured I'd post about it in case anyone has a similar issue.

---

