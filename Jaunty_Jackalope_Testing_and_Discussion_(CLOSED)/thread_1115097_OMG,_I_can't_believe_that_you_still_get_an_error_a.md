---
title: "OMG, I can't believe that you still get an error after burning a CD in Brasero"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hotweiss on 2009-04-03
OMG, I can't believe that you still get an error after burning a CD in Brasero. Everybody burns a CD's/DVD's, so everyone will get this error. This really makes Ubuntu look unpolished. I hope this bug gets taken care of by the final release.

---

### Post by Kow on 2009-04-03
> **hotweiss said:**
> OMG, I can't believe that you still get an error after burning a CD in Brasero. Everybody burns a CD's/DVD's, so everyone will get this error. This really makes Ubuntu look unpolished. I hope this bug gets taken care of by the final release.

... What error? Brasero has worked perfectly fine here since I started using it in hardy.

---

### Post by olskar on 2009-04-03
> **hotweiss said:**
> OMG, I can't believe that you still get an error after burning a CD in Brasero. Everybody burns a CD's/DVD's, so everyone will get this error.

That's a strange logic :) I don't get it, and propably not everyone trying to burn a CD either. It may depend on your burner, the cd or perhaps the files being burned? What is the error?

---

### Post by Therion on 2009-04-03
I burned two CD's and a DVD just last night in Brasero.  All three are fine...






/OP needs to chill, reassess.

---

### Post by kidux on 2009-04-03
The OP may be talking about the checksum it does after the burn. Clicking cancel on that produces an error IIRC.

---

### Post by hotweiss on 2009-04-03
LOL, I'm burning a DVD now just so I can get this error.

---

### Post by hotweiss on 2009-04-03
Checking session consistency (brasero_burn_check_session_consistency burn.c:1947)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_YJXRRU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=15
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_IESORU
	-exclude-list
	/tmp/brasero_tmp_A4SORU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_IESORU -exclude-list /tmp/brasero_tmp_A4SORU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 419248
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=15
	-use-the-force-luke=tracksize:419248
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_3GBQRU
	-exclude-list
	/tmp/brasero_tmp_SHBQRU
	-V
	Data disc (03 Apr 09)
	-A
	Brasero-0.8.4
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_3GBQRU -exclude-list /tmp/brasero_tmp_SHBQRU -V Data disc (03 Apr 09) -A Brasero-0.8.4 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr:   1.19% done, estimate finish Fri Apr  3 11:56:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   2.39% done, estimate finish Fri Apr  3 11:56:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   3.58% done, estimate finish Fri Apr  3 11:56:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr:   4.77% done, estimate finish Fri Apr  3 12:05:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   5.96% done, estimate finish Fri Apr  3 12:03:36 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   7.16% done, estimate finish Fri Apr  3 12:02:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   8.35% done, estimate finish Fri Apr  3 12:01:56 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   9.54% done, estimate finish Fri Apr  3 12:01:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  10.74% done, estimate finish Fri Apr  3 12:01:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  11.93% done, estimate finish Fri Apr  3 12:00:40 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  13.12% done, estimate finish Fri Apr  3 12:00:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  14.31% done, estimate finish Fri Apr  3 12:00:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  15.51% done, estimate finish Fri Apr  3 12:00:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  16.70% done, estimate finish Fri Apr  3 11:59:50 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  17.89% done, estimate finish Fri Apr  3 11:59:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  19.09% done, estimate finish Fri Apr  3 11:59:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  20.28% done, estimate finish Fri Apr  3 11:59:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  21.47% done, estimate finish Fri Apr  3 11:59:22 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  22.66% done, estimate finish Fri Apr  3 11:59:17 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  23.86% done, estimate finish Fri Apr  3 11:59:12 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  25.05% done, estimate finish Fri Apr  3 11:59:08 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  26.24% done, estimate finish Fri Apr  3 11:59:04 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  27.43% done, estimate finish Fri Apr  3 11:59:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  28.63% done, estimate finish Fri Apr  3 11:58:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  29.82% done, estimate finish Fri Apr  3 11:58:55 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  31.01% done, estimate finish Fri Apr  3 11:58:49 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  32.20% done, estimate finish Fri Apr  3 11:58:46 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  33.40% done, estimate finish Fri Apr  3 11:58:44 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  34.59% done, estimate finish Fri Apr  3 11:58:42 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  35.78% done, estimate finish Fri Apr  3 11:58:40 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  36.97% done, estimate finish Fri Apr  3 11:58:38 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  38.17% done, estimate finish Fri Apr  3 11:58:37 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  39.36% done, estimate finish Fri Apr  3 11:58:35 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  40.55% done, estimate finish Fri Apr  3 11:58:34 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  41.74% done, estimate finish Fri Apr  3 11:58:32 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  42.94% done, estimate finish Fri Apr  3 11:58:31 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  44.13% done, estimate finish Fri Apr  3 11:58:30 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  45.32% done, estimate finish Fri Apr  3 11:58:28 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  46.51% done, estimate finish Fri Apr  3 11:58:27 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  47.71% done, estimate finish Fri Apr  3 11:58:24 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  48.90% done, estimate finish Fri Apr  3 11:58:23 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  50.09% done, estimate finish Fri Apr  3 11:58:22 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  51.28% done, estimate finish Fri Apr  3 11:58:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  52.48% done, estimate finish Fri Apr  3 11:58:21 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  53.67% done, estimate finish Fri Apr  3 11:58:20 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  54.86% done, estimate finish Fri Apr  3 11:58:19 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  56.05% done, estimate finish Fri Apr  3 11:58:18 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  57.25% done, estimate finish Fri Apr  3 11:58:16 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  58.44% done, estimate finish Fri Apr  3 11:58:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  59.63% done, estimate finish Fri Apr  3 11:58:15 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  60.82% done, estimate finish Fri Apr  3 11:58:14 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  62.02% done, estimate finish Fri Apr  3 11:58:13 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  63.21% done, estimate finish Fri Apr  3 11:58:13 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  64.40% done, estimate finish Fri Apr  3 11:58:11 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  65.60% done, estimate finish Fri Apr  3 11:58:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  66.79% done, estimate finish Fri Apr  3 11:58:10 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  67.98% done, estimate finish Fri Apr  3 11:58:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  69.18% done, estimate finish Fri Apr  3 11:58:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  70.37% done, estimate finish Fri Apr  3 11:58:09 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  71.56% done, estimate finish Fri Apr  3 11:58:07 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  72.75% done, estimate finish Fri Apr  3 11:58:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  73.95% done, estimate finish Fri Apr  3 11:58:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  75.14% done, estimate finish Fri Apr  3 11:58:06 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  76.33% done, estimate finish Fri Apr  3 11:58:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  77.52% done, estimate finish Fri Apr  3 11:58:05 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  78.72% done, estimate finish Fri Apr  3 11:58:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  79.91% done, estimate finish Fri Apr  3 11:58:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  81.10% done, estimate finish Fri Apr  3 11:58:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  82.29% done, estimate finish Fri Apr  3 11:58:03 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  83.49% done, estimate finish Fri Apr  3 11:58:02 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  84.68% done, estimate finish Fri Apr  3 11:58:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  85.87% done, estimate finish Fri Apr  3 11:58:01 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  87.06% done, estimate finish Fri Apr  3 11:58:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  88.26% done, estimate finish Fri Apr  3 11:58:00 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  89.45% done, estimate finish Fri Apr  3 11:57:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  90.64% done, estimate finish Fri Apr  3 11:57:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  91.83% done, estimate finish Fri Apr  3 11:57:59 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  93.03% done, estimate finish Fri Apr  3 11:57:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  94.22% done, estimate finish Fri Apr  3 11:57:58 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  95.41% done, estimate finish Fri Apr  3 11:57:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  96.60% done, estimate finish Fri Apr  3 11:57:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  97.80% done, estimate finish Fri Apr  3 11:57:57 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:  98.99% done, estimate finish Fri Apr  3 11:57:56 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 347
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    419067
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 419098
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 419248 extents written (818 MB)
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: closing track
BraseroGrowisofs stderr: /dev/scd0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 0
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_error
BraseroChecksumFiles finished with an error
BraseroChecksumFiles asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroChecksumFiles stopping
Session error : unknown (brasero_burn_record burn.c:2644)

---

### Post by kansasnoob on 2009-04-03
Could you post a screenshot of the error?

I just burned some tax info to a data disc and all worked fine, and I also just burned the new Puppy iso, which also worked fine.

Never mind. You beat me to the punch.

I'm having to probs here though.

---

### Post by hotweiss on 2009-04-03
> **kansasnoob said:**
> Could you post a screenshot of the error?

I just burned some tax info to a data disc and all worked fine, and I also just burned the new Puppy iso, which also worked fine.

My previous reply has the error log...

I just installed Mint 64, but I got the same error in Ubuntu 9.04 beta.

---

### Post by Darkshade on 2009-04-03
I've burned over 20 CD's since I installed Jaunty and never had any problem or error.

---

### Post by golusweet on 2009-04-03
Brasero works fine.:p

---

### Post by uBeer on 2009-04-03
I have the same error on both of my machines: desktop and laptop. So hotweiss: you're not the only one.

It's annoying, but the cd's work, so I'm not that worried about it. It's just that this would scare new users...

---

### Post by forcecore on 2009-04-03
i can confirm that i have same error too ending with:

Session error : unknown (brasero_burn_record burn.c:2599)

still dvd is fine but these types of errors will scare lot of people so it MUST be fixed or IGNORED.

---

### Post by MaX on 2009-04-03
> **hotweiss said:**
> My previous reply has the error log...

I just installed Mint 64, but I got the same error in Ubuntu 9.04 beta.

Could edit the post and put the log in the code tags?

---

### Post by Seventh Reign on 2009-04-03
No errors here .. but I generally dont use Brasero for burning anyway.

---

### Post by olskar on 2009-04-03
Is a bug filed? I could not find one when searching launchpad. Sounds like a bug that should really be fixed if it is as common as it seems in this thread.

---

### Post by kansasnoob on 2009-04-03
I just burned two more data discs and no errors. Odd?

I'm not saying that your problem is not valid but I wonder if it's somehow hardware related?????????

My burner is SATA. I wonder if it varies from drive to drive????????? Difference between SATA and IDE?

---

### Post by Flywaver on 2009-04-03
I confirm that I have this SAME bug 99% of the time I burn a CD/DVD...and that's even at half-speed, not full speed! 	:mad:

Most CD/DVD work but I did encounter 2 faulty ones. Next time I will take a screenshot...really annoying!

---

### Post by biji on 2009-04-04
tried to burn dvd with jaunty... no error.. even i have tried multisession dvd with no error too

---

### Post by Darkshade on 2009-04-04
Ok, so that's 20 posts and no bug report #-o

---

### Post by mrwizer on 2009-04-04
Bug [report]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/354995")

---

### Post by mocoloco on 2009-04-04
I still don't get the point of Brasero, I find the built in Nautilus way much simpler.  All that was missing was making regular audio CDs, and the previous audio cd burner was fine.  Now you right click an iso and there are two "burn to disc" options, that's just confusing.

---

### Post by steeleyuk on 2009-04-04
Brasero has a plugin which replaces the nautilus-cd-burner. NCB has also been deprecated in 2.26.

---

### Post by Longinus00 on 2009-04-04
I had a similar problem that started when I replaced an IDE dvd burner for a SATA one last year. Interestingly enough, I could burn cds all day with brasero but it would almost never burn a dvd correctly. Different versions of ubuntu (hardy, etc.) and all the other popular burning programs (k3b, etc.) seemed to give the same failure as well. Booting into windows just to burn dvds is infuriating so I scoured the net for awhile until I stumbled upon the recommendation that I try Xfburn because it doesn't use whatever libraries for burning that those other programs are using. Lo and behold it worked. Xfburn may be a work in progress but at least it works at all.

TLDR, try Xfburn. :p

---

### Post by NewDisciple on 2009-04-04
I have discovered that I too get the same error dbug msg with Brasero.  I only found out because K3b errors out as well.

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
TSSTcorp CDDVDW SH-S223F SB00 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S223F '
Revision       : 'SB00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0017 (Reserved/Unknown) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1962752 = 1916 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1412 KB/s
Track 01: data   100 MB        
Total size:      115 MB (11:27.41) = 51556 sectors
Lout start:      115 MB (11:29/31) = 51556 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12508 (97:15/17)
  ATIP start of lead out: 359845 (79:59/70)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 22
Manufacturer: Ritek Co.
Blocks total: 359845 Blocks current: 359845 Blocks remaining: 308289
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.880s timeout 200s
Writing pregap for track 1 at -150
write track pad data: error after 0 bytes
BFree: 0 K BSize: 1916 K
Starting new track at sector: 0
Track 01:    0 of  100 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 200s
/usr/bin/wodim: The current problem looks like a buffer underrun.
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/wodim: Please report.
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 0 bytes
Writing  time:   15.676s
Average write speed 116.7x.
Fixating...
Fixating time:    0.002s
/usr/bin/wodim: fifo had 191 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -dao driveropts=burnfree -eject -data -tsize=51556s -

---

### Post by Flywaver on 2009-04-04
just burned the new parted magic 4 ISO...Brasero reported an error!

BraseroReadom stderr: Time total: 31.642sec
BraseroReadom stderr: Read 73906.00 kB at 2335.7 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 44bafedecddd5624bbcde5e754f99638 (3911b1a9c0a75c4322b2e41ba14c4d35 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record burn.c:2599)

---

### Post by kevpan815 on 2009-04-05
No Problems Here In 9.04 Beta, Just Fyi!

---

### Post by skiwithpete on 2009-04-05
I'm getting the error too

Session error : An internal error occurred (brasero_burn_record burn.c:2599)

YOU ARE NOT ALONE.

---

### Post by super.rad on 2009-04-05
Freash jaunty install, first time in ages I've had no errors at all from brasero

---

### Post by olskar on 2009-04-05
And still there is no one who confirmed the bug at [https://bugs.launchpad.net/bugs/354995](https://bugs.launchpad.net/bugs/354995)

:confused:

---

### Post by BigSilly on 2009-04-05
I get errors with Brasero too, which is why I use K3b. No problems with that.

---

### Post by Yashiro on 2009-04-05
The checksumming from within Brasero is bugged.

---

### Post by Flywaver on 2009-04-10
burned yet another CD...at the lowest possible speed, simulation was successful but got the dreaded error at the end of the burn:

BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 108.217sec
BraseroReadom stderr: Read 391926.00 kB at 3621.7 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 50d18664ce0e17fe85b822c2940f9be1 (b1eb856cebeb171512f1563f3fc03d57 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record burn.c:2599)

---

