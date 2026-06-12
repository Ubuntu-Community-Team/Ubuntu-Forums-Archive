---
title: "First Boot fails"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by boblemur on 2009-12-23
Hey,

I have just installed lynx in virtualbox the instillation went fine and the live cd runs perfectly.

However when i try and boot of the installed hard disk virtual box tells me that 

"A critical error has occurred while running the virtual machine and the machine execution has been stopped."

The only thing that comes up on the screen is:

Booting from local disk...
GRUB loading.

and then i get that message.

here is the log:
```
00:00:00.415 VirtualBox 3.0.8_OSE r53138 linux.amd64 (Oct 15 2009 05:04:01) release log
00:00:00.415 Log opened 2009-12-24T04:25:48.963012000Z
00:00:00.415 OS Product: Linux
00:00:00.415 OS Release: 2.6.31-16-generic
00:00:00.415 OS Version: #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009
00:00:00.415 Host RAM: 8002MB RAM, available: 7218MB
00:00:00.415 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.415 Process ID: 24976
00:00:00.415 Package type: LINUX_64BITS_GENERIC (OSE)
00:00:00.419 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xffffffffa0b96500 - ModuleInit at ffffffffa0ba83f0 and ModuleTerm at ffffffffa0ba83b0
00:00:00.419 SUP: VMMR0EntryEx located at ffffffffa0ba82d0, VMMR0EntryFast at ffffffffa0ba7610 and VMMR0EntryInt at ffffffffa0ba73e0
00:00:00.473 VBoxSharedClipboard mode: Bidirectional
00:00:00.556 OpenGL Info: Render SPU: GL_VENDOR:   NVIDIA Corporation
00:00:00.556 OpenGL Info: Render SPU: GL_RENDERER: Quadro FX 1700/PCI/SSE2
00:00:00.556 OpenGL Info: Render SPU: GL_VERSION:  3.0.0 NVIDIA 185.18.36
00:00:00.556 OpenGL Info: Render SPU: GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
00:00:00.558 Shared crOpenGL service loaded.
00:00:00.619 ************************* CFGM dump *************************
00:00:00.619 pRoot=0000000002222e40:{/}
00:00:00.619 [/] (level 0)
00:00:00.619   Name               <string>  = "Lucid" (cch=6)
00:00:00.619   UUID               <bytes>   = "9c 91 1a d6 fa 8a 8f 4f b5 e1 c3 12 6d 36 5f 92" (cb=16)
00:00:00.619   RamSize            <integer> = 0x00000000bb800000 (3145728000)
00:00:00.619   RamHoleSize        <integer> = 0x0000000020000000 (536870912)
00:00:00.619   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:00.619   TimerMillies       <integer> = 0x000000000000000a (10)
00:00:00.619   RawR3Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.619   RawR0Enabled       <integer> = 0x0000000000000001 (1)
00:00:00.619   PATMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.619   CSAMEnabled        <integer> = 0x0000000000000001 (1)
00:00:00.619   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
00:00:00.619   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:00.619   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:00.619   EnablePAE          <integer> = 0x0000000000000000 (0)
00:00:00.619 
00:00:00.619 [/HWVirtExt/] (level 1)
00:00:00.619 
00:00:00.619 [/PDM/] (level 1)
00:00:00.619 
00:00:00.619 [/PDM/Drivers/] (level 2)
00:00:00.619 
00:00:00.619 [/PDM/Drivers/VBoxC/] (level 3)
00:00:00.619   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:00.619 
00:00:00.619 [/Devices/] (level 1)
00:00:00.619 
00:00:00.619 [/Devices/pcarch/] (level 2)
00:00:00.619 
00:00:00.619 [/Devices/pcarch/0/] (level 3)
00:00:00.619   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.619 
00:00:00.619 [/Devices/pcarch/0/Config/] (level 4)
00:00:00.619 
00:00:00.619 [/Devices/pcbios/] (level 2)
00:00:00.619 
00:00:00.619 [/Devices/pcbios/0/] (level 3)
00:00:00.619   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.619 
00:00:00.619 [/Devices/pcbios/0/Config/] (level 4)
00:00:00.619   RamSize        <integer> = 0x00000000bb800000 (3145728000)
00:00:00.619   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:00.619   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:00.619   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:00.619   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:00.619   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:00.620   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:00.620   UUID           <bytes>   = "9c 91 1a d6 fa 8a 8f 4f b5 e1 c3 12 6d 36 5f 92" (cb=16)
00:00:00.620   BootDevice0    <string>  = "IDE" (cch=4)
00:00:00.620   BootDevice1    <string>  = "DVD" (cch=4)
00:00:00.620   BootDevice2    <string>  = "NONE" (cch=5)
00:00:00.620   BootDevice3    <string>  = "NONE" (cch=5)
00:00:00.620 
00:00:00.620 [/Devices/8237A/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/8237A/0/] (level 3)
00:00:00.620   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/pci/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/pci/0/] (level 3)
00:00:00.620   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/pci/0/Config/] (level 4)
00:00:00.620   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/] (level 3)
00:00:00.620   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/Config/] (level 4)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:00.620   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#0/Config/] (level 5)
00:00:00.620   QueueSize <integer> = 0x0000000000000040 (64)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.620   Driver <string>  = "MainKeyboard" (cch=13)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.620   Object <integer> = 0x00000000021e0530 (35521840)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:00.620   Driver <string>  = "MouseQueue" (cch=11)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#1/Config/] (level 5)
00:00:00.620   QueueSize <integer> = 0x0000000000000080 (128)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:00.620   Driver <string>  = "MainMouse" (cch=10)
00:00:00.620 
00:00:00.620 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6)
00:00:00.620   Object <integer> = 0x00000000021e0680 (35522176)
00:00:00.620 
00:00:00.620 [/Devices/i82078/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/] (level 3)
00:00:00.620   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/Config/] (level 4)
00:00:00.620   IRQ       <integer> = 0x0000000000000006 (6)
00:00:00.620   DMA       <integer> = 0x0000000000000002 (2)
00:00:00.620   MemMapped <integer> = 0x0000000000000000 (0)
00:00:00.620   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:00.620   Driver <string>  = "MainStatus" (cch=11)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/LUN#999/Config/] (level 5)
00:00:00.620   papLeds <integer> = 0x00000000021dfbe0 (35519456)
00:00:00.620   First   <integer> = 0x0000000000000000 (0)
00:00:00.620   Last    <integer> = 0x0000000000000000 (0)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:00.620   Driver <string>  = "Block" (cch=6)
00:00:00.620 
00:00:00.620 [/Devices/i82078/0/LUN#0/Config/] (level 5)
00:00:00.620   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:00.620   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/acpi/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/acpi/0/] (level 3)
00:00:00.620   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.620   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:00.620   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.620 
00:00:00.620 [/Devices/acpi/0/Config/] (level 4)
00:00:00.620   RamSize     <integer> = 0x00000000bb800000 (3145728000)
00:00:00.620   RamHoleSize <integer> = 0x0000000020000000 (536870912)
00:00:00.620   NumCPUs     <integer> = 0x0000000000000001 (1)
00:00:00.620   IOAPIC      <integer> = 0x0000000000000001 (1)
00:00:00.620   FdcEnabled  <integer> = 0x0000000000000001 (1)
00:00:00.620   ShowRtc     <integer> = 0x0000000000000000 (0)
00:00:00.620   ShowCpu     <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:00.620   Driver <string>  = "ACPIHost" (cch=9)
00:00:00.620 
00:00:00.620 [/Devices/acpi/0/LUN#0/Config/] (level 5)
00:00:00.620 
00:00:00.620 [/Devices/i8254/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/i8254/0/] (level 3)
00:00:00.620 
00:00:00.620 [/Devices/i8254/0/Config/] (level 4)
00:00:00.620 
00:00:00.620 [/Devices/i8259/] (level 2)
00:00:00.620 
00:00:00.620 [/Devices/i8259/0/] (level 3)
00:00:00.620   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.620 
00:00:00.620 [/Devices/i8259/0/Config/] (level 4)
00:00:00.621 
00:00:00.621 [/Devices/apic/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/apic/0/] (level 3)
00:00:00.621   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.621 
00:00:00.621 [/Devices/apic/0/Config/] (level 4)
00:00:00.621   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:00.621   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:00.621 
00:00:00.621 [/Devices/ioapic/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/ioapic/0/] (level 3)
00:00:00.621   Trusted <integer> = 0x0000000000000001 (1)
00:00:00.621 
00:00:00.621 [/Devices/ioapic/0/Config/] (level 4)
00:00:00.621 
00:00:00.621 [/Devices/mc146818/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/mc146818/0/] (level 3)
00:00:00.621 
00:00:00.621 [/Devices/mc146818/0/Config/] (level 4)
00:00:00.621 
00:00:00.621 [/Devices/vga/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/vga/0/] (level 3)
00:00:00.621   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.621   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:00.621   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.621 
00:00:00.621 [/Devices/vga/0/Config/] (level 4)
00:00:00.621   VRamSize         <integer> = 0x0000000003200000 (52428800)
00:00:00.621   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:00.621   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:00.621   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:00.621   LogoFile         <string>  = "" (cch=1)
00:00:00.621   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:00.621   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:00.621   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:00.621 
00:00:00.621 [/Devices/vga/0/LUN#0/] (level 4)
00:00:00.621   Driver <string>  = "MainDisplay" (cch=12)
00:00:00.621 
00:00:00.621 [/Devices/vga/0/LUN#0/Config/] (level 5)
00:00:00.621   Object <integer> = 0x00000000021e07d0 (35522512)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/] (level 3)
00:00:00.621   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.621   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:00.621   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/Config/] (level 4)
00:00:00.621   Type <string>  = "PIIX4" (cch=6)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:00.621   Driver <string>  = "MainStatus" (cch=11)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#999/Config/] (level 5)
00:00:00.621   papLeds <integer> = 0x00000000021dfbf0 (35519472)
00:00:00.621   First   <integer> = 0x0000000000000000 (0)
00:00:00.621   Last    <integer> = 0x0000000000000003 (3)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:00.621   Driver <string>  = "Block" (cch=6)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#2/Config/] (level 5)
00:00:00.621   Type      <string>  = "DVD" (cch=4)
00:00:00.621   Mountable <integer> = 0x0000000000000001 (1)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:00.621   Driver <string>  = "Block" (cch=6)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#0/Config/] (level 5)
00:00:00.621   Type      <string>  = "HardDisk" (cch=9)
00:00:00.621   Mountable <integer> = 0x0000000000000000 (0)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:00.621   Driver <string>  = "VD" (cch=3)
00:00:00.621 
00:00:00.621 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6)
00:00:00.621   Path   <string>  = "/home/nick/.VirtualBox/Machines/lucid/lucid.vdi" (cch=48)
00:00:00.621   Format <string>  = "VDI" (cch=4)
00:00:00.621 
00:00:00.621 [/Devices/pcnet/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/e1000/] (level 2)
00:00:00.621 
00:00:00.621 [/Devices/e1000/0/] (level 3)
00:00:00.621   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.621   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:00.621   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.621 
00:00:00.621 [/Devices/e1000/0/Config/] (level 4)
00:00:00.621   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:00.621   MAC            <bytes>   = "08 00 27 29 c0 0b" (cb=6)
00:00:00.621   CableConnected <integer> = 0x0000000000000001 (1)
00:00:00.621   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:00.621 
00:00:00.621 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:00.621   Driver <string>  = "MainStatus" (cch=11)
00:00:00.621 
00:00:00.621 [/Devices/e1000/0/LUN#999/Config/] (level 5)
00:00:00.622   papLeds <integer> = 0x00000000021dfd80 (35519872)
00:00:00.622 
00:00:00.622 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:00.622   Driver <string>  = "NAT" (cch=4)
00:00:00.622 
00:00:00.622 [/Devices/e1000/0/LUN#0/Config/] (level 5)
00:00:00.622   TFTPPrefix <string>  = "/home/nick/.VirtualBox/TFTP" (cch=28)
00:00:00.622   BootFile   <string>  = "Lucid.pxe" (cch=10)
00:00:00.622 
00:00:00.622 [/Devices/serial/] (level 2)
00:00:00.622 
00:00:00.622 [/Devices/parallel/] (level 2)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/] (level 2)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/] (level 3)
00:00:00.622   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.622   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:00.622   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/Config/] (level 4)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:00.622   Driver <string>  = "MainVMMDev" (cch=11)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/LUN#0/Config/] (level 5)
00:00:00.622   Object <integer> = 0x00000000021e0060 (35520608)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:00.622   Driver <string>  = "MainStatus" (cch=11)
00:00:00.622 
00:00:00.622 [/Devices/VMMDev/0/LUN#999/Config/] (level 5)
00:00:00.622   papLeds <integer> = 0x00000000021dfdc0 (35519936)
00:00:00.622   First   <integer> = 0x0000000000000000 (0)
00:00:00.622   Last    <integer> = 0x0000000000000000 (0)
00:00:00.622 
00:00:00.622 [/Devices/AudioSniffer/] (level 2)
00:00:00.622 
00:00:00.622 [/Devices/AudioSniffer/0/] (level 3)
00:00:00.622 
00:00:00.622 [/Devices/AudioSniffer/0/Config/] (level 4)
00:00:00.622 
00:00:00.622 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:00.622   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:00.622 
00:00:00.622 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5)
00:00:00.622   Object <integer> = 0x00000000021dff30 (35520304)
00:00:00.622 
00:00:00.622 [/Devices/ichac97/] (level 2)
00:00:00.622 
00:00:00.622 [/Devices/ichac97/0/] (level 3)
00:00:00.622   Trusted       <integer> = 0x0000000000000001 (1)
00:00:00.622   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:00.622   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:00.622 
00:00:00.622 [/Devices/ichac97/0/Config/] (level 4)
00:00:00.622 
00:00:00.622 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:00.622   Driver <string>  = "AUDIO" (cch=6)
00:00:00.622 
00:00:00.622 [/Devices/ichac97/0/LUN#0/Config/] (level 5)
00:00:00.622   AudioDriver <string>  = "pulse" (cch=6)
00:00:00.622   StreamName  <string>  = "Lucid" (cch=6)
00:00:00.622 
00:00:00.622 [/TM/] (level 1)
00:00:00.622   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:00.622 
00:00:00.622 ********************* End of CFGM dump **********************
00:00:00.622 MM: cbHyperHeap=0x140000 (1310720)
00:00:00.623 Logical host processors: 8, processor active mask: 00000000000000ff
00:00:00.623 ************************* CPUID dump ************************
00:00:00.623          RAW Standard CPUIDs
00:00:00.623      Function  eax      ebx      ecx      edx
00:00:00.624 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:00.624 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:00.624 Gst: 00000001  00010676 00000800 00000009 078bf1bf
00:00:00.624 Hst:           00010676 07040800 000ce3bd bfebfbff
00:00:00.624 Gst: 00000002  05b0b101 005657f0 00000000 2cb4304e
00:00:00.624 Hst:           05b0b101 005657f0 00000000 2cb4304e
00:00:00.624 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:00.624 Hst:           00000000 00000000 00000000 00000000
00:00:00.624 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:00.624 Hst:           0c000121 01c0003f 0000003f 00000001
00:00:00.624 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:00.624 Hst:           00000040 00000040 00000003 00002220
00:00:00.624 Name:                            GenuineIntel
00:00:00.624 Supports:                        0-5
00:00:00.624 Family:                          6  	Extended: 0 	Effective: 6
00:00:00.624 Model:                           7  	Extended: 1 	Effective: 23
00:00:00.624 Stepping:                        6
00:00:00.624 APIC ID:                         0x00
00:00:00.624 Logical CPUs:                    0
00:00:00.624 CLFLUSH Size:                    8
00:00:00.624 Brand ID:                        0x00
00:00:00.624 Mnemonic - Description                 = guest (host)
00:00:00.624 FPU - x87 FPU on Chip                  = 1 (1)
00:00:00.624 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:00.624 DE - Debugging extensions              = 1 (1)
00:00:00.624 PSE - Page Size Extension              = 1 (1)
00:00:00.624 TSC - Time Stamp Counter               = 1 (1)
00:00:00.624 MSR - Model Specific Registers         = 1 (1)
00:00:00.624 PAE - Physical Address Extension       = 0 (1)
00:00:00.624 MCE - Machine Check Exception          = 1 (1)
00:00:00.624 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:00.624 APIC - APIC On-Chip                    = 0 (1)
00:00:00.624 Reserved                               = 0 (0)
00:00:00.624 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:00.624 MTRR - Memory Type Range Registers     = 1 (1)
00:00:00.624 PGE - PTE Global Bit                   = 1 (1)
00:00:00.624 MCA - Machine Check Architecture       = 1 (1)
00:00:00.624 CMOV - Conditional Move Instructions   = 1 (1)
00:00:00.624 PAT - Page Attribute Table             = 1 (1)
00:00:00.624 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:00.624 PSN - Processor Serial Number          = 0 (0)
00:00:00.624 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:00.624 Reserved                               = 0 (0)
00:00:00.624 DS - Debug Store                       = 0 (1)
00:00:00.624 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:00.624 MMX - Intel MMX Technology             = 1 (1)
00:00:00.624 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:00.624 SSE - SSE Support                      = 1 (1)
00:00:00.624 SSE2 - SSE2 Support                    = 1 (1)
00:00:00.624 SS - Self Snoop                        = 0 (1)
00:00:00.624 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:00.624 TM - Thermal Monitor                   = 0 (1)
00:00:00.624 30 - Reserved                          = 0 (0)
00:00:00.624 PBE - Pending Break Enable             = 0 (1)
00:00:00.624 Supports SSE3 or not                   = 1 (1)
00:00:00.624 Reserved                               = 0 (0)
00:00:00.624 DS Area 64-bit layout                  = 0 (1)
00:00:00.624 Supports MONITOR/MWAIT                 = 1 (1)
00:00:00.624 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:00.624 VMX - Virtual Machine Technology       = 0 (1)
00:00:00.624 SMX - Safer Mode Extensions            = 0 (0)
00:00:00.624 Enhanced SpeedStep Technology          = 0 (1)
00:00:00.624 Terminal Monitor 2                     = 0 (1)
00:00:00.624 Supports Supplemental SSE3 or not      = 0 (1)
00:00:00.624 L1 Context ID                          = 0 (0)
00:00:00.624 Reserved                               = 0x0 (0x0)
00:00:00.624 CMPXCHG16B                             = 0 (1)
00:00:00.624 xTPR Update Control                    = 0 (1)
00:00:00.624 Perf/Debug Capability MSR              = 0 (1)
00:00:00.624 Reserved                               = 0x0 (0x0)
00:00:00.624 Direct Cache Access                    = 0 (1)
00:00:00.624 Supports SSE4_1 or not                 = 0 (1)
00:00:00.624 Supports SSE4_2 or not                 = 0 (0)
00:00:00.624 Supports the x2APIC extensions         = 0 (0)
00:00:00.624 Supports MOVBE                         = 0 (0)
00:00:00.624 Supports POPCNT                        = 0 (0)
00:00:00.624 Reserved                               = 0x0 (0x0)
00:00:00.624 Supports XSAVE                         = 0 (0)
00:00:00.624 Supports OSXSAVE                       = 0 (0)
00:00:00.624 Reserved                               = 0x0 (0x0)
00:00:00.624 
00:00:00.624          RAW Extended CPUIDs
00:00:00.624      Function  eax      ebx      ecx      edx
00:00:00.624 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:00.624 Hst:           80000008 00000000 00000000 00000000
00:00:00.624 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:00.624 Hst:           00000000 00000000 00000001 20100800
00:00:00.624 Gst: 80000002  65746e49 2952286c 6f655820 2952286e
00:00:00.624 Hst:           65746e49 2952286c 6f655820 2952286e
00:00:00.624 Gst: 80000003  55504320 20202020 20202020 58202020
00:00:00.624 Hst:           55504320 20202020 20202020 58202020
00:00:00.624 Gst: 80000004  30363435 20402020 36312e33 007a4847
00:00:00.624 Hst:           30363435 20402020 36312e33 007a4847
00:00:00.624 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:00.624 Hst:           00000000 00000000 00000000 00000000
00:00:00.624 Gst: 80000006  00000000 00000000 18008040 00000000
00:00:00.624 Hst:           00000000 00000000 18008040 00000000
00:00:00.624 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:00.624 Hst:           00000000 00000000 00000000 00000000
00:00:00.624 Gst: 80000008  00003026 00000000 00000000 00000000
00:00:00.624 Hst:           00003026 00000000 00000000 00000000
00:00:00.624 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:00.624 Hst:           07280202 00000000 00000000 00000503
00:00:00.624 Ext Name:                        
00:00:00.624 Ext Supports:                    0x80000000-0x80000008
00:00:00.624 Family:                          0  	Extended: 0 	Effective: 0
00:00:00.624 Model:                           0  	Extended: 0 	Effective: 0
00:00:00.624 Stepping:                        0
00:00:00.624 Brand ID:                        0x000
00:00:00.624 Mnemonic - Description                 = guest (host)
00:00:00.624 FPU - x87 FPU on Chip                  = 0 (0)
00:00:00.624 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:00.624 DE - Debugging extensions              = 0 (0)
00:00:00.624 PSE - Page Size Extension              = 0 (0)
00:00:00.624 TSC - Time Stamp Counter               = 0 (0)
00:00:00.624 MSR - K86 Model Specific Registers     = 0 (0)
00:00:00.624 PAE - Physical Address Extension       = 0 (0)
00:00:00.624 MCE - Machine Check Exception          = 0 (0)
00:00:00.624 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:00.624 APIC - APIC On-Chip                    = 0 (0)
00:00:00.624 10 - Reserved                          = 0 (0)
00:00:00.624 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:00.624 MTRR - Memory Type Range Registers     = 0 (0)
00:00:00.624 PGE - PTE Global Bit                   = 0 (0)
00:00:00.624 MCA - Machine Check Architecture       = 0 (0)
00:00:00.624 CMOV - Conditional Move Instructions   = 0 (0)
00:00:00.624 PAT - Page Attribute Table             = 0 (0)
00:00:00.624 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:00.624 18 - Reserved                          = 0 (0)
00:00:00.624 19 - Reserved                          = 0 (0)
00:00:00.624 NX - No-Execute Page Protection        = 0 (1)
00:00:00.624 DS - Debug Store                       = 0 (0)
00:00:00.624 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:00.624 MMX - Intel MMX Technology             = 0 (0)
00:00:00.624 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:00.624 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:00.624 26 - 1 GB large page support           = 0 (0)
00:00:00.624 27 - RDTSCP instruction                = 0 (0)
00:00:00.624 28 - Reserved                          = 0 (0)
00:00:00.624 29 - AMD Long Mode                     = 0 (1)
00:00:00.624 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:00.624 31 - AMD 3DNow                         = 0 (0)
00:00:00.624 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:00.624 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:00.624 SVM - AMD VM Extensions                = 0 (0)
00:00:00.624 APIC registers starting at 0x400       = 0 (0)
00:00:00.624 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:00.624 Advanced bit manipulation              = 0 (0)
00:00:00.624 SSE4A instruction support              = 0 (0)
00:00:00.624 Misaligned SSE mode                    = 0 (0)
00:00:00.624 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:00.624 OS visible workaround                  = 0 (0)
00:00:00.624 Instruction based sampling             = 0 (0)
00:00:00.624 SSE5 support                           = 0 (0)
00:00:00.624 SKINIT, STGI, and DEV support          = 0 (0)
00:00:00.624 Watchdog timer support.                = 0 (0)
00:00:00.624 31:14 - Reserved                       = 0x0 (0x0)
00:00:00.624 Full Name:                       Intel(R) Xeon(R) CPU           X5460  @ 3.16GHz
00:00:00.624 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:00.624 TLB 2/4M Data:                   res0     0 entries
00:00:00.624 TLB 4K Instr/Uni:                res0     0 entries
00:00:00.624 TLB 4K Data:                     res0     0 entries
00:00:00.624 L1 Instr Cache Line Size:        0 bytes
00:00:00.624 L1 Instr Cache Lines Per Tag:    0
00:00:00.624 L1 Instr Cache Associativity:    res0  
00:00:00.624 L1 Instr Cache Size:             0 KB
00:00:00.624 L1 Data Cache Line Size:         0 bytes
00:00:00.624 L1 Data Cache Lines Per Tag:     0
00:00:00.624 L1 Data Cache Associativity:     res0  
00:00:00.624 L1 Data Cache Size:              0 KB
00:00:00.624 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:00.624 L2 TLB 2/4M Data:                off       0 entries
00:00:00.624 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:00.624 L2 TLB 4K Data:                  off       0 entries
00:00:00.624 L2 Cache Line Size:              0 bytes
00:00:00.624 L2 Cache Lines Per Tag:          0
00:00:00.624 L2 Cache Associativity:          off   
00:00:00.624 L2 Cache Size:                   0 KB
00:00:00.624 APM Features:                   
00:00:00.624 Physical Address Width:          38 bits
00:00:00.624 Virtual Address Width:           48 bits
00:00:00.624 Physical Core Count:             0
00:00:00.624 
00:00:00.624          RAW Centaur CPUIDs
00:00:00.624      Function  eax      ebx      ecx      edx
00:00:00.624 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:00.624 Hst:           07280202 00000000 00000000 00000503
00:00:00.624 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:00.624 Hst:           07280202 00000000 00000000 00000503
00:00:00.624 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:00.624 Hst:           07280202 00000000 00000000 00000503
00:00:00.624 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:00.624 Hst:           07280202 00000000 00000000 00000503
00:00:00.624 Centaur Supports:                0xc0000000-0x07280202
00:00:00.624 Mnemonic - Description                 = guest (host)
00:00:00.624 AIS - Alternate Instruction Set        = 0 (1)
00:00:00.624 AIS-E - AIS enabled                    = 0 (1)
00:00:00.624 RNG - Random Number Generator          = 0 (0)
00:00:00.624 RNG-E - RNG enabled                    = 0 (0)
00:00:00.624 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:00.624 FEMMS - FEMMS                          = 0 (0)
00:00:00.624 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:00.624 ACE-E - ACE enabled                    = 0 (0)
00:00:00.624 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:00.624 ACE2-E - ACE enabled                   = 0 (0)
00:00:00.624 PHE - Hash Engine                      = 0 (1)
00:00:00.624 PHE-E - PHE enabled                    = 0 (0)
00:00:00.624 PMM - Montgomery Multiplier            = 0 (0)
00:00:00.624 PMM-E - PMM enabled                    = 0 (0)
00:00:00.624 
00:00:00.624 
00:00:00.624 ******************** End of CPUID dump **********************
00:00:00.625 Debug: HCPhysInterPD=0000000085c04000 HCPhysInterPaePDPT=0000000033394000 HCPhysInterPaePML4=0000000091d02000
00:00:00.625 Debug: apInterPTs={000000007a2d6000,000000007a2d7000} apInterPaePTs={00000001f9272000,00000001eb943000} apInterPaePDs={00000001fa7a6000,00000001f9308000,00000001f9270000,00000001f9279000} pInterPaePDPT64=0000000033395000
00:00:00.657 TM: GIP - u32Mode=1 (SyncTSC) u32UpdateHz=100
00:00:00.690 TM: cTSCTicksPerSecond=0xbc44c570 (3 158 623 600) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:00.690 TM: fMaybeUseOffsettedHostTSC=true  TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:00.690 CoreCode: R3=00007f7098cd1000 R0=ffffc90000c7b000 RC=a0d68000 Phys=0000000058b39000 cb=0x1000
00:00:00.694 [SMP] BIOS with 1 CPUs
00:00:00.704 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xffffffffa0c05480 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.707 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xffffffffa0c16420 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:00.707 Activating Local APIC
00:00:00.707 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:00.707 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:00.707 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.711 Shared Folders service loaded.
00:00:00.732 VDInit finished
00:00:00.732 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 16777216
00:00:00.732 PIIX3 ATA: LUN#1: no unit
00:00:00.733 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 0, passthrough disabled
00:00:00.733 PIIX3 ATA: LUN#3: no unit
00:00:00.733 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.833 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.933 NAT: adding domain name home to search list
00:00:00.933 NAT: value of BindIP has been ignored
00:00:00.933 Audio: Trying driver 'pulse'.
00:00:00.938 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:00.938 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:00.940 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:00.940 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:00.942 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:00.944 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:00.944 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:00.959 HWACCM: No VT-x or AMD-V CPU extension found. Reason VERR_VMX_MSR_LOCKED_OR_DISABLED
00:00:00.960 HWACCM: VMX MSR_IA32_FEATURE_CONTROL=1
00:00:00.973 VM: Halt method global1 (5)
00:00:00.973 Changing the VM state from 'CREATING' to 'CREATED'.
00:00:00.973 Changing the VM state from 'CREATED' to 'RUNNING'.
00:00:00.977 Guest Log: BIOS: VirtualBox 3.0.8_OSE
00:00:00.977 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:00.989 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.989 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:00.991 Guest Log: BIOS: ata0-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:00.991 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:00.991 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:00.992 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:00.994 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f7094b37000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:03.470 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=0000000000000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:03.475 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.478 Guest Log: BIOS: Booting from Hard Disk...
00:00:03.485 PIIX3 ATA: Ctl#0: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.485 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:03.611 
00:00:03.611 Trying to execute code with memory type addr_code=000000010000c020 addend=00007f6f98495000 at 000000010000ca42! (iHandlerMemType=0x38 iMMIOMemType=0x30 IOTLB=0000000000000010)
00:00:03.611 *** handlers
00:00:03.611 Physical handlers: (PhysHandlers=63040 (0xf640))
00:00:03.611 From     - To (incl) HandlerHC UserHC    HandlerGC UserGC    Type     Description
00:00:03.611 00000000000a0000 - 00000000000bffff  00007f709fd92980  00007f709a2be6f0  ff79f8b0  fe8436f0  MMIO     VGA - VGA Video Buffer
00:00:03.611 00000000000c0000 - 00000000000c8fff  00007f709fd4d440  00007f709a2be8d0  ff7bac20  fe8438d0  Write    VGA BIOS
00:00:03.611 00000000000e0000 - 00000000000e0fff  00007f709fd4d440  00007f709a2c6910  ff7bac20  fe84b910  Write    ACPI RSDP
00:00:03.611 00000000000e1000 - 00000000000e1fff  00007f709fd4d440  00007f709a2b54f0  ff7bac20  fe83a4f0  Write    DMI tables
00:00:03.611 00000000000e2000 - 00000000000e6fff  00007f709fd4d440  00007f709a2b5df0  ff7bac20  fe83adf0  All      Net Boot ROM
00:00:03.611 00000000000f0000 - 00000000000fffff  00007f709fd4d440  00007f709a2b55f0  ff7bac20  fe83a5f0  Write    PC BIOS - 0xfffff
00:00:03.611 00000000e0000000 - 00000000e31fffff  00007f70987a6b40  00007f7097d370c0  ff7eb340  ff7fe0c0  Write    VGA LFB
00:00:03.611 00000000f0000000 - 00000000f001ffff  00007f709fd92980  00007f709a2c7250  ff79f8b0  fe84c250  MMIO     E1000
00:00:03.611 00000000fec00000 - 00000000fec00fff  00007f709fd92980  00007f709a2b82a0  ff79f8b0  fe83d2a0  MMIO     I/O APIC Memory
00:00:03.611 00000000fee00000 - 00000000fee00fff  00007f709fd92980  00007f709a2b7ed0  ff79f8b0  fe83ced0  MMIO     APIC Memory
00:00:03.611 00000000ffff0000 - 00000000ffffffff  00007f709fd4d440  00007f709a2b5940  ff7bac20  fe83a940  Write    PC BIOS - 0xffffffff
00:00:03.611 Virtual handlers:
00:00:03.611 From     - To (excl) HandlerHC HandlerGC Type     Description
00:00:03.611 Hypervisor Virtual handlers:
00:00:03.611 From     - To (excl) HandlerHC HandlerGC Type     Description
00:00:03.611 00000000fe808190 - 00000000fe80898f  0000000000000000  ff795a20  WriteHyp   Shadow IDT write access handler
00:00:03.611 00000000fe8096b0 - 00000000fe809737  0000000000000000  ff795300  WriteHyp   Shadow TSS write access handler
00:00:03.611 00000000ff56a000 - 00000000ff579fff  0000000000000000  ff795420  WriteHyp   Shadow GDT write access handler
00:00:03.611 00000000ff57b000 - 00000000ff58bfff  0000000000000000  ff795390  WriteHyp   Shadow LDT write access handler
00:00:03.611 *** mmio
00:00:03.611 MMIO ranges (pVM=00007f70a47b0000)
00:00:03.611 GC Phys Range                     pDevIns          Read             Write            Fill             pvUser           Description
00:00:03.611 00000000000a0000-00000000000bffff 00007f7097d37000 00007f70987a7ef0 00007f70987a7440 00007f70987a5cb0 0000000000000000 VGA - VGA Video Buffer
00:00:03.611                                R0 00007f7097d37000 ffffffffa0c06d10 ffffffffa0c074c0 ffffffffa0c06260 0000000000000000
00:00:03.611                                RC ff7fe000 ff7ea860 ff7ea480 ff7eaac0 00000000
00:00:03.611 00000000f0000000-00000000f001ffff 00007f709a2c02a0 00007f7098776be0 00007f7098776210 0000000000000000 0000000000000000 E1000
00:00:03.611                                R0 00007f709a2c02a0 ffffffffa0c0e050 ffffffffa0c0d770 0000000000000000 0000000000000000
00:00:03.611                                RC fe8452a0 ff7f1b30 ff7f1260 00000000 00000000
00:00:03.611 00000000fec00000-00000000fec00fff 00007f709a2b80e0 00007f709852bcf0 00007f709852be80 0000000000000000 00007f709a2b81a0 I/O APIC Memory
00:00:03.611                                R0 00007f709a2b80e0 ffffffffa0c16790 ffffffffa0c168b0 0000000000000000 0000000000000000
00:00:03.611                                RC fe83d0e0 ff7fa360 ff7fa480 00000000 00000000
00:00:03.611 00000000fee00000-00000000fee00fff 00007f709a2b7bb0 00007f709852d660 00007f709852e1c0 0000000000000000 00007f709a2b7c70 APIC Memory
00:00:03.611                                R0 00007f709a2b7bb0 ffffffffa0c17120 ffffffffa0c17ac0 0000000000000000 0000000000000000
00:00:03.611                                RC fe83cbb0 ff7fada0 ff7fb6d0 00000000 00000000
00:00:03.611 *** phys
00:00:03.611 RAM ranges (pVM=00007f70a47b0000)
00:00:03.611 GC Phys Range                     pvHC            
00:00:03.611 0000000000000000-00000000bb7fffff 0000000000000000 Base RAM
00:00:03.611 00000000e0000000-00000000e31fffff 00007f7094b37000 VRam
00:00:03.611 00000000f0000000-00000000f001ffff 0000000000000000 E1000
00:00:03.611 00000000f0400000-00000000f07fffff 00007f7097fd7000 VMMDev
00:00:03.611 00000000f0800000-00000000f0803fff 00007f7097fd3000 VMMDev Heap
00:00:03.611 00000000fec00000-00000000fec00fff 0000000000000000 I/O APIC Memory
00:00:03.611 00000000fee00000-00000000fee00fff 0000000000000000 APIC Memory
00:00:03.611 00000000ffff0000-00000000ffffffff 0000000000000000 PC BIOS - 0xffffffff
00:00:03.612 fatal error in recompiler cpu: Trying to execute code with memory type addr_code=000000010000c020 addend=00007f6f98495000 at 000000010000ca42. (iHandlerMemType=0x38 iMMIOMemType=0x30)
00:00:03.612 
00:00:03.612 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:03.612 !!
00:00:03.612 !!                 Guru Meditation -2301 (VERR_REM_VIRTUAL_CPU_ERROR)
00:00:03.612 !!
00:00:03.612 !!
00:00:03.612 !! {mappings, <NULL>}
00:00:03.612 !!
00:00:03.612 
00:00:03.612 The mappings are FLOATING.
00:00:03.612 00000000fe800000 - 00000000ffbfffff  Hypervisor Memory Area
00:00:03.612 !!
00:00:03.612 !! {hma, <NULL>}
00:00:03.612 !!
00:00:03.612 Hypervisor Memory Area (HMA) Layout: Base 00000000fe800000, 0x01400000 bytes
00:00:03.612 00000000ff918000-00000000ff919000                                   DYNAMIC                  fence
00:00:03.612 00000000ff909000-00000000ff918000 00007f708f07f000 00007f708f07f000 LOCKED                   alloc once (PGM_MAPPINGS)
00:00:03.612 00000000ff908000-00000000ff909000                                   DYNAMIC                  fence
00:00:03.612 00000000ff8f8000-00000000ff908000                                   DYNAMIC                  Dynamic mapping
00:00:03.612 00000000ff8f7000-00000000ff8f8000                                   DYNAMIC                  fence
00:00:03.612 00000000ff8d7000-00000000ff8f7000 00007f7094a92000 00007f7094a92000 LOCKED                   alloc once (PDM_DEVICE_USER)
00:00:03.612 00000000ff8d6000-00000000ff8d7000                                   DYNAMIC                  fence
00:00:03.612 00000000ff8c6000-00000000ff8d6000 00007f7094ad3000 00007f7094ad3000 LOCKED                   alloc once (PDM_DEVICE_USER)
00:00:03.612 00000000ff846000-00000000ff8c6000                                   MMIO2   0000000000000000 VGA VRam
00:00:03.612 00000000ff845000-00000000ff846000                                   DYNAMIC                  fence
00:00:03.612 00000000ff812000-00000000ff845000 00007f7094b04000 00007f7094b04000 LOCKED                   alloc once (PGM_PHYS)
00:00:03.612 00000000ff811000-00000000ff812000                                   DYNAMIC                  fence
00:00:03.612 00000000ff7fe000-00000000ff811000 00007f7097d37000 00007f7097d37000 LOCKED                   alloc once (PDM_DEVICE)
00:00:03.612 00000000ff7fd000-00000000ff7fe000                                   DYNAMIC                  fence
00:00:03.612 00000000ff7fa000-00000000ff7fd000 00007f70983d7000 0000000000000000 LOCKED                   VBoxDD2GC.gc
00:00:03.612 00000000ff7f9000-00000000ff7fa000                                   DYNAMIC                  fence
00:00:03.612 00000000ff7e9000-00000000ff7f9000 00007f70983da000 0000000000000000 LOCKED                   VBoxDDGC.gc
00:00:03.612 00000000ff7e8000-00000000ff7e9000                                   DYNAMIC                  fence
00:00:03.612 00000000ff794000-00000000ff7e8000 00007f7098a56000 0000000000000000 LOCKED                   VMMGC.gc
00:00:03.612 00000000ff793000-00000000ff794000                                   DYNAMIC                  fence
00:00:03.612 00000000ff58d000-00000000ff793000 00007f7098aaa000 00007f7098aaa000 LOCKED                   alloc once (PATM)
00:00:03.612 00000000ff58c000-00000000ff58d000                                   DYNAMIC                  fence
00:00:03.612 00000000ff57b000-00000000ff58c000 00007f7098cb0000 00007f7098cb0000 LOCKED                   alloc once (SELM)
00:00:03.612 00000000ff57a000-00000000ff57b000                                   DYNAMIC                  fence
00:00:03.612 00000000ff56a000-00000000ff57a000 00007f7098cc1000 00007f7098cc1000 LOCKED                   alloc once (SELM)
00:00:03.612 00000000ff569000-00000000ff56a000                                   DYNAMIC                  fence
00:00:03.612 00000000ff568000-00000000ff569000 00007f7098cd1000 ffffc90000c7b000 HCPHYS  0000000058b39000 Core Code
00:00:03.612 00000000ff567000-00000000ff568000                                   DYNAMIC                  fence
00:00:03.612 00000000ff566000-00000000ff567000 00007f70b4989000 0000000000000000 HCPHYS  00000000964e4000 GIP
00:00:03.612 00000000ff565000-00000000ff566000                                   DYNAMIC                  fence
00:00:03.612 00000000fe9ac000-00000000ff565000 00007f7098d53000 00007f7098d53000 LOCKED                   alloc once (PGM_PHYS)
00:00:03.612 00000000fe9ab000-00000000fe9ac000                                   DYNAMIC                  fence
00:00:03.612 00000000fe972000-00000000fe9ab000 00007f709a1cd000 00007f709a1cd000 LOCKED                   alloc once (PGM_POOL)
00:00:03.612 00000000fe971000-00000000fe972000                                   DYNAMIC                  fence
00:00:03.612 00000000fe96c000-00000000fe971000                                   DYNAMIC                  CR3 mapping
00:00:03.612 00000000fe96b000-00000000fe96c000                                   DYNAMIC                  fence
00:00:03.613 00000000fe82b000-00000000fe96b000 00007f709a2a6000 00007f709a2a6000 LOCKED                   Heap
00:00:03.613 00000000fe82a000-00000000fe82b000                                   DYNAMIC                  fence
00:00:03.613 00000000fe801000-00000000fe82a000 00007f70a47b0000 ffffc90011990000 LOCKED                   VM
00:00:03.613 00000000fe800000-00000000fe801000                                   DYNAMIC                  fence
00:00:03.613 !!
00:00:03.613 !! {cpumguest, verbose}
00:00:03.613 !!
00:00:03.613 Guest CPUM (VCPU 0) state: se
00:00:03.613 eax=00068000 ebx=0010fa68 ecx=00000023 edx=00000000 esi=0010a4dc edi=0001a354
00:00:03.613 eip=0000ca42 esp=0007fec0 ebp=0007fefc iopl=0         nv up di pl zr na pe nc
00:00:03.613 cs={0008 base=0000000000000000 limit=ffffffff flags=0000c09a} dr0=00000000 dr1=00000000
00:00:03.613 ds={0010 base=0000000000000000 limit=ffffffff flags=0000c093} dr2=00000000 dr3=00000000
00:00:03.613 es={0010 base=0000000000000000 limit=ffffffff flags=0000c093} dr4=00000000 dr5=00000000
00:00:03.613 fs={0010 base=0000000000000000 limit=ffffffff flags=0000c093} dr6=ffff0ff0 dr7=00000400
00:00:03.613 gs={0010 base=0000000000000000 limit=ffffffff flags=0000c093} cr0=60000011 cr2=00000000
00:00:03.613 ss={0010 base=0000000000000000 limit=ffffffff flags=0000c093} cr3=00000000 cr4=00000000
00:00:03.613 gdtr=0000000000008340:0027  idtr=0000000000000000:ffff  eflags=00200002
00:00:03.613 ldtr={0000 base=00000000 limit=0000ffff flags=00000082}
00:00:03.613 tr  ={0000 base=00000000 limit=0000ffff flags=00000083}
00:00:03.613 SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:03.613 FPU:
00:00:03.613 FCW=037f FSW=0000 FTW=00
00:00:03.613 res1=00 FOP=0000 FPUIP=00000000 CS=0000 Rsvrd1=0000
00:00:03.613 FPUDP=0000 DS=0000 Rsvrd2=0000 MXCSR=00001f80 MXCSR_MASK=00000000
00:00:03.613 MSR:
00:00:03.613 EFER         =0000000000000000
00:00:03.613 PAT          =0007040600070406
00:00:03.613 STAR         =0000000000000000
00:00:03.613 CSTAR        =0000000000000000
00:00:03.613 LSTAR        =0000000000000000
00:00:03.613 SFMASK       =0000000000000000
00:00:03.613 KERNELGSBASE =0000000000000000
00:00:03.613 !!
00:00:03.613 !! {cpumguestinstr, verbose}
00:00:03.613 !!
00:00:03.613 !!
00:00:03.613 !! {cpumhyper, verbose}
00:00:03.613 !!
00:00:03.613 Hypervisor CPUM state: se
00:00:03.613 .eax=00000000 .ebx=00000000 .ecx=00000000 .edx=00000000 .esi=fe801340 .edi=00000014
00:00:03.613 .eip=00000000 .esp=fe96a000 .ebp=00000000 .iopl=0           nv up di pl zr na pe nc
00:00:03.613 .cs={fff8 base=0000000000000000 limit=00000000 flags=00000000} .dr0=00000000 .dr1=00000000
00:00:03.613 .ds={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr2=00000000 .dr3=00000000
00:00:03.613 .es={fff0 base=0000000000000000 limit=00000000 flags=00000000} .dr4=00000000 .dr5=00000000
00:00:03.613 .fs={0000 base=0000000000000000 limit=00000000 flags=00000000} .dr6=00000000 .dr7=00000000
00:00:03.613 .gs={0000 base=0000000000000000 limit=00000000 flags=00000000} .cr0=00000000 .cr2=00000000
00:00:03.613 .ss={fff0 base=0000000000000000 limit=00000000 flags=00000000} .cr3=62a06000 .cr4=00000000
00:00:03.613 .gdtr=00000000ff56a000:ffff  .idtr=00000000fe808190:07ff  .eflags=00000000
00:00:03.613 .ldtr={0000 base=00000000 limit=00000000 flags=00000000}
00:00:03.613 .tr  ={ffe0 base=00000000 limit=00000000 flags=00000000}
00:00:03.613 .SysEnter={cs=0000 eip=00000000 esp=00000000}
00:00:03.613 FPU:
00:00:03.613 .FCW=0000 .FSW=0000 .FTW=00
00:00:03.613 .res1=00 .FOP=0000 .FPUIP=00000000 .CS=0000 .Rsvrd1=0000
00:00:03.613 .FPUDP=0000 .DS=0000 .Rsvrd2=0000 .MXCSR=00000000 .MXCSR_MASK=00000000
00:00:03.613 MSR:
00:00:03.613 .EFER         =0000000000000000
00:00:03.613 .PAT          =0000000000000000
00:00:03.613 .STAR         =0000000000000000
00:00:03.613 .CSTAR        =0000000000000000
00:00:03.613 .LSTAR        =0000000000000000
00:00:03.613 .SFMASK       =0000000000000000
00:00:03.613 .KERNELGSBASE =0000000000000000
00:00:03.613 CR4OrMask=0x204 CR4AndMask=0x403
00:00:03.613 !!
00:00:03.613 !! {cpumhost, verbose}
00:00:03.613 !!
00:00:03.613 Host CPUM state: se
00:00:03.613 rax=xxxxxxxxxxxxxxxx rbx=ffffc90011990000 rcx=xxxxxxxxxxxxxxxx
00:00:03.613 rdx=xxxxxxxxxxxxxxxx rsi=ffff8801010a9d27 rdi=ffffc90011990000
00:00:03.613 rip=xxxxxxxxxxxxxxxx rsp=ffff8801010a9cf0 rbp=ffff8801010a9d48
00:00:03.613  r8=xxxxxxxxxxxxxxxx  r9=xxxxxxxxxxxxxxxx r10=0000000000040000
00:00:03.613 r11=0000000000000000 r12=ffffffffa0d22480 r13=0000000000000206
00:00:03.613 r14=ffff8801eb83b390 r15=ffff88020115cc00
00:00:03.613 iopl=0          nv up di pl nz na po nc
00:00:03.613 cs=0000  ds=0000  es=0000  fs=0000  gs=0000                   eflags=00000046
00:00:03.613 cr0=0000000080050033 cr2=xxxxxxxxxxxxxxxx cr3=00000001965dc000
00:00:03.613 cr4=00000000000006e0 ldtr=0000 tr=0040
00:00:03.613 dr[0]=0000000000000000 dr[1]=0000000000000000 dr[2]=0000000000000000
00:00:03.613 dr[3]=0000000000000000 dr[6]=0000000000000000 dr[7]=0000000000000000
00:00:03.613 gdtr=ffff88002810a000:007f  idtr=ffffffff818fd000:0fff
00:00:03.613 SysEnter={cs=0010 eip=00000000 esp=00000000}
00:00:03.613 FSbase=00007f709d1a0910 GSbase=ffff880028106000 efer=00000d01
00:00:03.613 !!
00:00:03.613 !! {mode, all}
00:00:03.613 !!
00:00:03.613 Guest paging mode:  Protected, changed 15 times, A20 enabled
00:00:03.613 Shadow paging mode: PAE
00:00:03.613 Host paging mode:   AMD64+G+NX
00:00:03.613 !!
00:00:03.613 !! {cpuid, verbose}
00:00:03.613 !!
00:00:03.613          RAW Standard CPUIDs
00:00:03.613      Function  eax      ebx      ecx      edx
00:00:03.613 Gst: 00000000  00000005 756e6547 6c65746e 49656e69
00:00:03.613 Hst:           0000000a 756e6547 6c65746e 49656e69
00:00:03.613 Gst: 00000001  00010676 00000800 00000009 078bf3bf
00:00:03.613 Hst:           00010676 03040800 000ce3bd bfebfbff
00:00:03.613 Gst: 00000002  05b0b101 005657f0 00000000 2cb4304e
00:00:03.613 Hst:           05b0b101 005657f0 00000000 2cb4304e
00:00:03.613 Gst: 00000003  00000000 00000000 00000000 00000000
00:00:03.613 Hst:           00000000 00000000 00000000 00000000
00:00:03.613 Gst: 00000004  00000000 00000000 00000000 00000000
00:00:03.613 Hst:           0c000121 01c0003f 0000003f 00000001
00:00:03.613 Gst: 00000005  00000040 00000040 00000000 00000000
00:00:03.613 Hst:           00000040 00000040 00000003 00002220
00:00:03.613 Name:                            GenuineIntel
00:00:03.613 Supports:                        0-5
00:00:03.613 Family:                          6  	Extended: 0 	Effective: 6
00:00:03.613 Model:                           7  	Extended: 1 	Effective: 23
00:00:03.613 Stepping:                        6
00:00:03.613 APIC ID:                         0x00
00:00:03.613 Logical CPUs:                    0
00:00:03.613 CLFLUSH Size:                    8
00:00:03.613 Brand ID:                        0x00
00:00:03.613 Mnemonic - Description                 = guest (host)
00:00:03.613 FPU - x87 FPU on Chip                  = 1 (1)
00:00:03.613 VME - Virtual 8086 Mode Enhancements   = 1 (1)
00:00:03.613 DE - Debugging extensions              = 1 (1)
00:00:03.613 PSE - Page Size Extension              = 1 (1)
00:00:03.613 TSC - Time Stamp Counter               = 1 (1)
00:00:03.613 MSR - Model Specific Registers         = 1 (1)
00:00:03.613 PAE - Physical Address Extension       = 0 (1)
00:00:03.613 MCE - Machine Check Exception          = 1 (1)
00:00:03.613 CX8 - CMPXCHG8B instruction            = 1 (1)
00:00:03.613 APIC - APIC On-Chip                    = 1 (1)
00:00:03.613 Reserved                               = 0 (0)
00:00:03.613 SEP - SYSENTER and SYSEXIT             = 0 (1)
00:00:03.613 MTRR - Memory Type Range Registers     = 1 (1)
00:00:03.613 PGE - PTE Global Bit                   = 1 (1)
00:00:03.613 MCA - Machine Check Architecture       = 1 (1)
00:00:03.613 CMOV - Conditional Move Instructions   = 1 (1)
00:00:03.613 PAT - Page Attribute Table             = 1 (1)
00:00:03.613 PSE-36 - 36-bit Page Size Extention    = 1 (1)
00:00:03.613 PSN - Processor Serial Number          = 0 (0)
00:00:03.613 CLFSH - CLFLUSH Instruction.           = 1 (1)
00:00:03.613 Reserved                               = 0 (0)
00:00:03.613 DS - Debug Store                       = 0 (1)
00:00:03.613 ACPI - Thermal Mon. & Soft. Clock Ctrl.= 0 (1)
00:00:03.613 MMX - Intel MMX Technology             = 1 (1)
00:00:03.613 FXSR - FXSAVE and FXRSTOR Instructions = 1 (1)
00:00:03.613 SSE - SSE Support                      = 1 (1)
00:00:03.613 SSE2 - SSE2 Support                    = 1 (1)
00:00:03.613 SS - Self Snoop                        = 0 (1)
00:00:03.613 HTT - Hyper-Threading Technolog        = 0 (1)
00:00:03.613 TM - Thermal Monitor                   = 0 (1)
00:00:03.613 30 - Reserved                          = 0 (0)
00:00:03.613 PBE - Pending Break Enable             = 0 (1)
00:00:03.613 Supports SSE3 or not                   = 1 (1)
00:00:03.613 Reserved                               = 0 (0)
00:00:03.613 DS Area 64-bit layout                  = 0 (1)
00:00:03.613 Supports MONITOR/MWAIT                 = 1 (1)
00:00:03.613 CPL-DS - CPL Qualified Debug Store     = 0 (1)
00:00:03.613 VMX - Virtual Machine Technology       = 0 (1)
00:00:03.613 SMX - Safer Mode Extensions            = 0 (0)
00:00:03.613 Enhanced SpeedStep Technology          = 0 (1)
00:00:03.613 Terminal Monitor 2                     = 0 (1)
00:00:03.613 Supports Supplemental SSE3 or not      = 0 (1)
00:00:03.613 L1 Context ID                          = 0 (0)
00:00:03.613 Reserved                               = 0x0 (0x0)
00:00:03.613 CMPXCHG16B                             = 0 (1)
00:00:03.613 xTPR Update Control                    = 0 (1)
00:00:03.613 Perf/Debug Capability MSR              = 0 (1)
00:00:03.613 Reserved                               = 0x0 (0x0)
00:00:03.613 Direct Cache Access                    = 0 (1)
00:00:03.613 Supports SSE4_1 or not                 = 0 (1)
00:00:03.613 Supports SSE4_2 or not                 = 0 (0)
00:00:03.613 Supports the x2APIC extensions         = 0 (0)
00:00:03.613 Supports MOVBE                         = 0 (0)
00:00:03.613 Supports POPCNT                        = 0 (0)
00:00:03.613 Reserved                               = 0x0 (0x0)
00:00:03.613 Supports XSAVE                         = 0 (0)
00:00:03.613 Supports OSXSAVE                       = 0 (0)
00:00:03.613 Reserved                               = 0x0 (0x0)
00:00:03.613 
00:00:03.613          RAW Extended CPUIDs
00:00:03.613      Function  eax      ebx      ecx      edx
00:00:03.613 Gst: 80000000  80000008 00000000 00000000 00000000
00:00:03.614 Hst:           80000008 00000000 00000000 00000000
00:00:03.614 Gst: 80000001  00000000 00000000 00000000 00000000
00:00:03.614 Hst:           00000000 00000000 00000001 20100800
00:00:03.614 Gst: 80000002  65746e49 2952286c 6f655820 2952286e
00:00:03.614 Hst:           65746e49 2952286c 6f655820 2952286e
00:00:03.614 Gst: 80000003  55504320 20202020 20202020 58202020
00:00:03.614 Hst:           55504320 20202020 20202020 58202020
00:00:03.614 Gst: 80000004  30363435 20402020 36312e33 007a4847
00:00:03.614 Hst:           30363435 20402020 36312e33 007a4847
00:00:03.614 Gst: 80000005  00000000 00000000 00000000 00000000
00:00:03.614 Hst:           00000000 00000000 00000000 00000000
00:00:03.614 Gst: 80000006  00000000 00000000 18008040 00000000
00:00:03.614 Hst:           00000000 00000000 18008040 00000000
00:00:03.614 Gst: 80000007  00000000 00000000 00000000 00000000
00:00:03.614 Hst:           00000000 00000000 00000000 00000000
00:00:03.614 Gst: 80000008  00003026 00000000 00000000 00000000
00:00:03.614 Hst:           00003026 00000000 00000000 00000000
00:00:03.614 Gst: 80000009  07280202 00000000 00000000 00000503*
00:00:03.614 Hst:           07280202 00000000 00000000 00000503
00:00:03.614 Ext Name:                        
00:00:03.614 Ext Supports:                    0x80000000-0x80000008
00:00:03.614 Family:                          0  	Extended: 0 	Effective: 0
00:00:03.614 Model:                           0  	Extended: 0 	Effective: 0
00:00:03.614 Stepping:                        0
00:00:03.614 Brand ID:                        0x000
00:00:03.614 Mnemonic - Description                 = guest (host)
00:00:03.614 FPU - x87 FPU on Chip                  = 0 (0)
00:00:03.614 VME - Virtual 8086 Mode Enhancements   = 0 (0)
00:00:03.614 DE - Debugging extensions              = 0 (0)
00:00:03.614 PSE - Page Size Extension              = 0 (0)
00:00:03.614 TSC - Time Stamp Counter               = 0 (0)
00:00:03.614 MSR - K86 Model Specific Registers     = 0 (0)
00:00:03.614 PAE - Physical Address Extension       = 0 (0)
00:00:03.614 MCE - Machine Check Exception          = 0 (0)
00:00:03.614 CX8 - CMPXCHG8B instruction            = 0 (0)
00:00:03.614 APIC - APIC On-Chip                    = 0 (0)
00:00:03.614 10 - Reserved                          = 0 (0)
00:00:03.614 SEP - SYSCALL and SYSRET               = 0 (1)
00:00:03.614 MTRR - Memory Type Range Registers     = 0 (0)
00:00:03.614 PGE - PTE Global Bit                   = 0 (0)
00:00:03.614 MCA - Machine Check Architecture       = 0 (0)
00:00:03.614 CMOV - Conditional Move Instructions   = 0 (0)
00:00:03.614 PAT - Page Attribute Table             = 0 (0)
00:00:03.614 PSE-36 - 36-bit Page Size Extention    = 0 (0)
00:00:03.614 18 - Reserved                          = 0 (0)
00:00:03.614 19 - Reserved                          = 0 (0)
00:00:03.614 NX - No-Execute Page Protection        = 0 (1)
00:00:03.614 DS - Debug Store                       = 0 (0)
00:00:03.614 AXMMX - AMD Extensions to MMX Instr.   = 0 (0)
00:00:03.614 MMX - Intel MMX Technology             = 0 (0)
00:00:03.614 FXSR - FXSAVE and FXRSTOR Instructions = 0 (0)
00:00:03.614 25 - AMD fast FXSAVE and FXRSTOR Instr.= 0 (0)
00:00:03.614 26 - 1 GB large page support           = 0 (0)
00:00:03.614 27 - RDTSCP instruction                = 0 (0)
00:00:03.614 28 - Reserved                          = 0 (0)
00:00:03.614 29 - AMD Long Mode                     = 0 (1)
00:00:03.614 30 - AMD Extensions to 3DNow           = 0 (0)
00:00:03.614 31 - AMD 3DNow                         = 0 (0)
00:00:03.614 LahfSahf - LAHF/SAHF in 64-bit mode    = 0 (1)
00:00:03.614 CmpLegacy - Core MP legacy mode (depr) = 0 (0)
00:00:03.614 SVM - AMD VM Extensions                = 0 (0)
00:00:03.614 APIC registers starting at 0x400       = 0 (0)
00:00:03.614 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 0 (0)
00:00:03.614 Advanced bit manipulation              = 0 (0)
00:00:03.614 SSE4A instruction support              = 0 (0)
00:00:03.614 Misaligned SSE mode                    = 0 (0)
00:00:03.614 PREFETCH and PREFETCHW instruction     = 0 (0)
00:00:03.614 OS visible workaround                  = 0 (0)
00:00:03.614 Instruction based sampling             = 0 (0)
00:00:03.614 SSE5 support                           = 0 (0)
00:00:03.614 SKINIT, STGI, and DEV support          = 0 (0)
00:00:03.614 Watchdog timer support.                = 0 (0)
00:00:03.614 31:14 - Reserved                       = 0x0 (0x0)
00:00:03.614 Full Name:                       Intel(R) Xeon(R) CPU           X5460  @ 3.16GHz
00:00:03.614 TLB 2/4M Instr/Uni:              res0     0 entries
00:00:03.614 TLB 2/4M Data:                   res0     0 entries
00:00:03.614 TLB 4K Instr/Uni:                res0     0 entries
00:00:03.614 TLB 4K Data:                     res0     0 entries
00:00:03.614 L1 Instr Cache Line Size:        0 bytes
00:00:03.614 L1 Instr Cache Lines Per Tag:    0
00:00:03.614 L1 Instr Cache Associativity:    res0  
00:00:03.614 L1 Instr Cache Size:             0 KB
00:00:03.614 L1 Data Cache Line Size:         0 bytes
00:00:03.614 L1 Data Cache Lines Per Tag:     0
00:00:03.614 L1 Data Cache Associativity:     res0  
00:00:03.614 L1 Data Cache Size:              0 KB
00:00:03.614 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:03.614 L2 TLB 2/4M Data:                off       0 entries
00:00:03.614 L2 TLB 4K Instr/Uni:             off       0 entries
00:00:03.614 L2 TLB 4K Data:                  off       0 entries
00:00:03.614 L2 Cache Line Size:              0 bytes
00:00:03.614 L2 Cache Lines Per Tag:          0
00:00:03.614 L2 Cache Associativity:          off   
00:00:03.614 L2 Cache Size:                   0 KB
00:00:03.614 APM Features:                   
00:00:03.614 Physical Address Width:          38 bits
00:00:03.614 Virtual Address Width:           48 bits
00:00:03.614 Physical Core Count:             0
00:00:03.614 
00:00:03.614          RAW Centaur CPUIDs
00:00:03.614      Function  eax      ebx      ecx      edx
00:00:03.614 Gst: c0000000  07280202 00000000 00000000 00000503
00:00:03.614 Hst:           07280202 00000000 00000000 00000503
00:00:03.614 Gst: c0000001  07280202 00000000 00000000 00000503
00:00:03.614 Hst:           07280202 00000000 00000000 00000503
00:00:03.614 Gst: c0000002  07280202 00000000 00000000 00000503
00:00:03.614 Hst:           07280202 00000000 00000000 00000503
00:00:03.614 Gst: c0000003  07280202 00000000 00000000 00000503
00:00:03.614 Hst:           07280202 00000000 00000000 00000503
00:00:03.614 Centaur Supports:                0xc0000000-0x07280202
00:00:03.614 Mnemonic - Description                 = guest (host)
00:00:03.614 AIS - Alternate Instruction Set        = 0 (1)
00:00:03.614 AIS-E - AIS enabled                    = 0 (1)
00:00:03.614 RNG - Random Number Generator          = 0 (0)
00:00:03.614 RNG-E - RNG enabled                    = 0 (0)
00:00:03.614 LH - LongHaul MSR 0000_110Ah           = 0 (0)
00:00:03.614 FEMMS - FEMMS                          = 0 (0)
00:00:03.614 ACE - Advanced Cryptography Engine     = 0 (0)
00:00:03.614 ACE-E - ACE enabled                    = 0 (0)
00:00:03.614 ACE2 - Advanced Cryptography Engine 2  = 0 (1)
00:00:03.614 ACE2-E - ACE enabled                   = 0 (0)
00:00:03.614 PHE - Hash Engine                      = 0 (1)
00:00:03.614 PHE-E - PHE enabled                    = 0 (0)
00:00:03.614 PMM - Montgomery Multiplier            = 0 (0)
00:00:03.614 PMM-E - PMM enabled                    = 0 (0)
00:00:03.614 
00:00:03.614 !!
00:00:03.614 !! {gdt, <NULL>}
00:00:03.614 !!
00:00:03.614 Shadow GDT (GCAddr=ff56a000):
00:00:03.614 ffd8 - 97380087 fe008980 - base=fe809738 limit=00000087 dpl=0 TSS32Avail Present 16-bit  HyperTSSTrap08
00:00:03.614 ffe0 - 96b00087 fe008b80 - base=fe8096b0 limit=00000087 dpl=0 TSS32Busy Present 16-bit  HyperTSS
00:00:03.614 ffe8 - 0000ffff 00af9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 16-bit  HyperCS64
00:00:03.614 fff0 - 0000ffff 00cf9300 - base=00000000 limit=ffffffff dpl=0 DataRW Accessed Present Page 32-bit  HyperDS
00:00:03.614 fff8 - 0000ffff 00cf9b00 - base=00000000 limit=ffffffff dpl=0 CodeER Accessed Present Page 32-bit  HyperCS
00:00:03.614 !!
00:00:03.614 !! {ldt, <NULL>}
00:00:03.614 !!
00:00:03.614 Shadow LDT (GCAddr=ff57b000 limit=0x0):
00:00:03.614 !!
00:00:03.614 !! {ioport, <NULL>}
00:00:03.614 !!
00:00:03.614 I/O Port R3 ranges (pVM=00007f70a47b0000)
00:00:03.614 Range     pDevIns          In               Out              pvUser           Description
00:00:03.614 0000-0000 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0001-0001 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0002-0002 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0003-0003 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0004-0004 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0005-0005 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0006-0006 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0007-0007 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004acb0 DMA
00:00:03.614 0008-0008 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 0009-0009 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000a-000a 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000b-000b 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000c-000c 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000d-000d 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000e-000e 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 000f-000f 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004acb0 DMA cont
00:00:03.614 0020-0021 00007f709a2b7620 00007f70987948c0 00007f7098794d40 0000000000000000 i8259 PIC #0
00:00:03.614 0040-0043 00007f709a2b8430 00007f70987957d0 00007f70987958f0 0000000000000000 i8254 Programmable Interval Timer
00:00:03.614 0060-0060 00007f709a2b6fd0 00007f70987ae5a0 00007f70987ae770 0000000000000000 PC Keyboard - Data
00:00:03.614 0061-0061 00007f709a2b8430 00007f7098795260 00007f70987955a0 0000000000000000 PC Speaker
00:00:03.614 0064-0064 00007f709a2b6fd0 00007f70987ae260 00007f70987ae2e0 0000000000000000 PC Keyboard - Command / Status
00:00:03.614 0070-0071 00007f709a2b88a0 00007f7098790670 00007f70987911f0 0000000000000000 MC146818 RTC/CMOS
00:00:03.614 0081-0081 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004acb0 DMA Page
00:00:03.614 0082-0082 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004acb0 DMA Page
00:00:03.614 0083-0083 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004acb0 DMA Page
00:00:03.614 0087-0087 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004acb0 DMA Page
00:00:03.614 0089-0089 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004ad58 DMA Page
00:00:03.614 008a-008a 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004ad58 DMA Page
00:00:03.614 008b-008b 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004ad58 DMA Page
00:00:03.614 008f-008f 00007f70a004abe0 00007f709877e4b0 00007f709877e390 00007f70a004ad58 DMA Page
00:00:03.614 0092-0092 00007f70a00441a0 00007f709878d360 00007f709878d3a0 0000000000000000 PS/2 system control port A (A20 and more)
00:00:03.614 00a0-00a1 00007f709a2b7620 00007f70987948c0 00007f7098794d40 0000000000000001 i8259 PIC #1
00:00:03.614 00c0-00c0 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00c2-00c2 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00c4-00c4 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00c6-00c6 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00c8-00c8 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00ca-00ca 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00cc-00cc 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00ce-00ce 00007f70a004abe0 00007f709877e420 00007f709877e300 00007f70a004ad58 DMA
00:00:03.614 00d0-00d0 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00d2-00d2 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00d4-00d4 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00d6-00d6 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00d8-00d8 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00da-00da 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.614 00dc-00dc 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.615 00de-00de 00007f70a004abe0 00007f709877e530 00007f709877e3f0 00007f70a004ad58 DMA cont
00:00:03.615 00f0-00ff 00007f70a00441a0 00007f709878d320 00007f709878d330 0000000000000000 Math Co-Processor (DOS/OS2 mode)
00:00:03.615 0170-0177 00007f709a2bed90 00007f709879d970 00007f709879e9d0 0000000000000001 ATA I/O Base 1
00:00:03.615 01ce-01ce 00007f7097d37000 00007f70987a6780 00007f70987a6870 0000000000000000 VGA/VBE - Index
00:00:03.615 01cf-01cf 00007f7097d37000 00007f70987a6430 00007f70987a6660 0000000000000000 VGA/VBE - Data
00:00:03.615 01f0-01f7 00007f709a2bed90 00007f709879d970 00007f709879e9d0 0000000000000000 ATA I/O Base 1
00:00:03.615 0376-0376 00007f709a2bed90 00007f7098798f00 00007f709879bce0 0000000000000001 ATA I/O Base 2
00:00:03.615 03b4-03b5 00007f7097d37000 00007f70987a6960 00007f70987a6a20 0000000000000000 VGA - 3b4
00:00:03.615 03b6-03b6 00007f7097d37000 00007f70987a5aa0 00007f70987a5ba0 0000000000000000 VBE BIOS Extra Data
00:00:03.615 03b7-03b7 00007f7097d37000 00007f70987a3360 00007f70987a5c20 0000000000000000 VGA BIOS debug/panic
00:00:03.615 03b8-03b8 00007f7097d37000 00007f70987a3a90 00007f70987a3840 0000000000000000 BIOS Logo
00:00:03.615 03ba-03ba 00007f7097d37000 00007f70987a6960 00007f70987a6a20 0000000000000000 VGA - 3ba
00:00:03.615 03c0-03cf 00007f7097d37000 00007f70987a6960 00007f70987a6a20 0000000000000000 VGA - 3c0
00:00:03.615 03d4-03d5 00007f7097d37000 00007f70987a6960 00007f70987a6a20 0000000000000000 VGA - 3d4
00:00:03.615 03da-03da 00007f7097d37000 00007f70987a6960 00007f70987a6a20 0000000000000000 VGA - 3da
00:00:03.615 03f1-03f5 00007f70a0053030 00007f709877c590 00007f709877cc70 00007f70a00530f0 FDC#1
00:00:03.615 03f6-03f6 00007f709a2bed90 00007f7098798f00 00007f709879bce0 0000000000000000 ATA I/O Base 2
00:00:03.615 03f7-03f7 00007f70a0053030 00007f709877c590 00007f709877cc70 00007f70a00530f0 FDC#2
00:00:03.615 0400-0403 00007f70a09637f0 00007f709878d5d0 00007f709878dce0 0000000000000000 Bochs PC BIOS - Panic & Debug
00:00:03.615 04d0-04d0 00007f709a2b7620 00007f7098793b20 00007f7098793b90 00007f709a2b76e0 i8259 PIC #0 - elcr
00:00:03.615 04d1-04d1 00007f709a2b7620 00007f7098793b20 00007f7098793b90 00007f709a2b7708 i8259 PIC #1 - elcr
00:00:03.615 0504-0504 00007f70a09a7330 00007f709fd67bf0 00007f709878b240 0000000000000000 VMMDev backdoor logging
00:00:03.615 0505-0505 00007f70a09a7330 00007f709878a940 00007f709878a900 0000000000000000 VMMDev timesync backdoor
00:00:03.615 0cf8-0cf8 00007f709a2b5f90 00007f70987aaea0 00007f70987aae30 0000000000000000 i440FX (PCI)
00:00:03.615 0cfc-0cff 00007f709a2b5f90 00007f70987aafa0 00007f70987aaf10 0000000000000000 i440FX (PCI)
00:00:03.615 4000-4000 00007f709a2c5550 00007f7098791f80 00007f7098792010 00007f709a2c5610 ACPI PM1a Status
00:00:03.615 4002-4002 00007f709a2c5550 00007f7098791f50 00007f7098791fe0 00007f709a2c5610 ACPI PM1a Enable
00:00:03.615 4004-4004 00007f709a2c5550 00007f7098791fb0 00007f70987922e0 00007f709a2c5610 ACPI PM1a Control
00:00:03.615 4008-4008 00007f709a2c5550 00007f70987921b0 00007f709fd668a0 00007f709a2c5610 ACPI PM Timer
00:00:03.615 4020-4020 00007f709a2c5550 00007f7098792060 00007f70987920c0 00007f709a2c5610 ACPI GPE0 Status
00:00:03.615 4021-4021 00007f709a2c5550 00007f7098792090 00007f70987920f0 00007f709a2c5610 ACPI GPE0 Enable
00:00:03.615 4040-4040 00007f709a2c5550 00007f709fd67bf0 00007f7098791be0 00007f709a2c5610 ACPI Battery status index
00:00:03.615 4044-4044 00007f709a2c5550 00007f7098791c30 00007f709fd668a0 00007f709a2c5610 ACPI Battery status data
00:00:03.615 4048-4048 00007f709a2c5550 00007f709fd67bf0 00007f7098791d60 00007f709a2c5610 ACPI system info index
00:00:03.615 404c-404c 00007f709a2c5550 00007f7098791de0 00007f7098791f00 00007f709a2c5610 ACPI system info data
00:00:03.615 4050-4050 00007f709a2c5550 00007f709fd67bf0 00007f7098792150 00007f709a2c5610 ACPI Reset
00:00:03.615 442e-442e 00007f709a2c5550 00007f709fd67bf0 00007f7098792110 00007f709a2c5610 ACPI SMI
00:00:03.615 8900-8900 00007f70a09637f0 00007f709878d5d0 00007f709878dce0 0000000000000000 Bochs PC BIOS - Shutdown
00:00:03.615 d000-d007 00007f709a2bed90 00007f7098799000 00007f7098799140 0000000000000000 ATA Bus Master DMA
00:00:03.615 d008-d00f 00007f709a2bed90 00007f7098799000 00007f7098799140 0000000000000001 ATA Bus Master DMA
00:00:03.615 d010-d017 00007f709a2c02a0 00007f7098776c00 00007f7098776250 0000000000000000 E1000
00:00:03.615 d020-d020 00007f70a09a7330 00007f709fd67bf0 00007f709878bfc0 00007f70a09a73f0 VMMDev Request Handler
00:00:03.615 d100-d1ff 00007f70a0065030 00007f7098781a90 00007f70987833b0 00007f70a00650f0 ICHAC97 NAM
00:00:03.615 d200-d23f 00007f70a0065030 00007f7098781820 00007f7098781c10 00007f70a00650f0 ICHAC97 NABM
00:00:03.615 I/O Port R0 ranges (pVM=00007f70a47b0000)
00:00:03.615 Range     pDevIns          In               Out              pvUser           Description
00:00:03.615 0020-0021 00007f709a2b7620 ffffffffa0c097b0 ffffffffa0c09c60 0000000000000000 i8259 PIC #0
00:00:03.615 0040-0043 00007f709a2b8430 ffffffffa0c09320 ffffffffa0c09150 0000000000000000 i8254 Programmable Interval Timer
00:00:03.615 0060-0060 00007f709a2b6fd0 ffffffffa0c08430 ffffffffa0c08600 0000000000000000 PC Keyboard - Data
00:00:03.615 0064-0064 00007f709a2b6fd0 ffffffffa0c083b0 ffffffffa0c080f0 0000000000000000 PC Keyboard - Command / Status
00:00:03.615 0070-0071 00007f709a2b88a0 ffffffffa0c09fc0 ffffffffa0c0a3d0 0000000000000000 MC146818 RTC/CMOS
00:00:03.615 00a0-00a1 00007f709a2b7620 ffffffffa0c097b0 ffffffffa0c09c60 0000000000000001 i8259 PIC #1
00:00:03.615 0170-0177 00007f709a2bed90 ffffffffa0c0b020 ffffffffa0c0b170 0000000000000001 ATA I/O Base 1
00:00:03.615 01ce-01ce 00007f7097d37000 ffffffffa0c05d90 ffffffffa0c060b0 0000000000000000 VGA/VBE - Index (GC)
00:00:03.615 01cf-01cf 00007f7097d37000 ffffffffa0c05e80 ffffffffa0c07a70 0000000000000000 VGA/VBE - Data (GC)
00:00:03.615 01f0-01f7 00007f709a2bed90 ffffffffa0c0b020 ffffffffa0c0b170 0000000000000000 ATA I/O Base 1
00:00:03.615 0376-0376 00007f709a2bed90 ffffffffa0c0a820 ffffffffa0c0abd0 0000000000000001 ATA I/O Base 2
00:00:03.615 03b4-03b5 00007f7097d37000 ffffffffa0c061a0 ffffffffa0c07e90 0000000000000000 VGA - 3b4 (GC)
00:00:03.615 03b7-03b7 00007f7097d37000 ffffffffa0c05cf0 ffffffffa0c05d00 0000000000000000 VGA BIOS debug/panic
00:00:03.615 03ba-03ba 00007f7097d37000 ffffffffa0c061a0 ffffffffa0c07e90 0000000000000000 VGA - 3ba (GC)
00:00:03.615 03c0-03cf 00007f7097d37000 ffffffffa0c061a0 ffffffffa0c07e90 0000000000000000 VGA - 3c0 (GC)
00:00:03.615 03d4-03d5 00007f7097d37000 ffffffffa0c061a0 ffffffffa0c07e90 0000000000000000 VGA - 3d4 (GC)
00:00:03.615 03da-03da 00007f7097d37000 ffffffffa0c061a0 ffffffffa0c07e90 0000000000000000 VGA - 3da (GC)
00:00:03.615 03f6-03f6 00007f709a2bed90 ffffffffa0c0a820 ffffffffa0c0abd0 0000000000000000 ATA I/O Base 2
00:00:03.615 04d0-04d0 00007f709a2b7620 ffffffffa0c094f0 ffffffffa0c09560 00007f709a2b76e0 i8259 PIC #0 - elcr
00:00:03.615 04d1-04d1 00007f709a2b7620 ffffffffa0c094f0 ffffffffa0c09560 00007f709a2b7708 i8259 PIC #1 - elcr
00:00:03.615 0cf8-0cf8 00007f709a2b5f90 ffffffffa0c058f0 ffffffffa0c05880 0000000000000000 i440FX (PCI)
00:00:03.615 0cfc-0cff 00007f709a2b5f90 ffffffffa0c05a10 ffffffffa0c05960 0000000000000000 i440FX (PCI)
00:00:03.615 4008-4008 00007f709a2c5550 ffffffffa0c08e10 0000000000000000 0000000000000000 ACPI PM Timer
00:00:03.615 d000-d007 00007f709a2bed90 ffffffffa0c0aa80 ffffffffa0c0a910 0000000000000000 ATA Bus Master DMA
00:00:03.615 d008-d00f 00007f709a2bed90 ffffffffa0c0aa80 ffffffffa0c0a910 0000000000000001 ATA Bus Master DMA
00:00:03.615 d010-d017 00007f709a2c02a0 ffffffffa0c0dff0 ffffffffa0c0d7b0 0000000000000000 E1000
00:00:03.615 I/O Port GC ranges (pVM=00007f70a47b0000)
00:00:03.615 Range     pDevIns  In       Out      pvUser   Description
00:00:03.615 0020-0021 fe83c620 ff7ecf90 ff7ed430 00000000 i8259 PIC #0
00:00:03.615 0040-0043 fe83d430 ff7ecb50 ff7ec9e0 00000000 i8254 Programmable Interval Timer
00:00:03.615 0060-0060 fe83bfd0 ff7ebc40 ff7ebdf0 00000000 PC Keyboard - Data
00:00:03.615 0061-0061 fe83d430 ff7ec7a0 00000000 00000000 PC Speaker
00:00:03.615 0064-0064 fe83bfd0 ff7ebbd0 ff7eb940 00000000 PC Keyboard - Command / Status
00:00:03.615 0070-0071 fe83d8a0 ff7ed760 ff7edc40 00000000 MC146818 RTC/CMOS
00:00:03.615 00a0-00a1 fe83c620 ff7ecf90 ff7ed430 00000001 i8259 PIC #1
00:00:03.615 0170-0177 fe843d90 ff7eeaa0 ff7eec00 00000001 ATA I/O Base 1
00:00:03.615 01ce-01ce ff7fe000 ff7e9c00 ff7e9ee0 00000000 VGA/VBE - Index (GC)
00:00:03.615 01cf-01cf ff7fe000 ff7e9ce0 ff7e9fb0 00000000 VGA/VBE - Data (GC)
00:00:03.615 01f0-01f7 fe843d90 ff7eeaa0 ff7eec00 00000000 ATA I/O Base 1
00:00:03.615 0376-0376 fe843d90 ff7ee0d0 ff7ee6c0 00000001 ATA I/O Base 2
00:00:03.615 03b4-03b5 ff7fe000 ff7ea0b0 ff7eb6e0 00000000 VGA - 3b4 (GC)
00:00:03.615 03ba-03ba ff7fe000 ff7ea0b0 ff7eb6e0 00000000 VGA - 3ba (GC)
00:00:03.615 03c0-03cf ff7fe000 ff7ea0b0 ff7eb6e0 00000000 VGA - 3c0 (GC)
00:00:03.615 03d4-03d5 ff7fe000 ff7ea0b0 ff7eb6e0 00000000 VGA - 3d4 (GC)
00:00:03.615 03da-03da ff7fe000 ff7ea0b0 ff7eb6e0 00000000 VGA - 3da (GC)
00:00:03.615 03f6-03f6 fe843d90 ff7ee0d0 ff7ee6c0 00000000 ATA I/O Base 2
00:00:03.615 04d0-04d0 fe83c620 ff7ecd00 ff7ecd60 fe83c6e0 i8259 PIC #0 - elcr
00:00:03.615 04d1-04d1 fe83c620 ff7ecd00 ff7ecd60 fe83c708 i8259 PIC #1 - elcr
00:00:03.615 0cf8-0cf8 fe83af90 ff7e9450 ff7e93f0 00000000 i440FX (PCI)
00:00:03.615 0cfc-0cff fe83af90 ff7e9560 ff7e94c0 00000000 i440FX (PCI)
00:00:03.615 4008-4008 fe84a550 ff7ec580 00000000 00000000 ACPI PM Timer
00:00:03.615 d000-d007 fe843d90 ff7ee300 ff7ee1b0 00000000 ATA Bus Master DMA
00:00:03.615 d008-d00f fe843d90 ff7ee300 ff7ee1b0 00000001 ATA Bus Master DMA
00:00:03.615 d010-d017 fe8452a0 ff7f1ab0 ff7f12b0 00000000 E1000
00:00:03.615 R3 Read  Ports: 0x61-0x62 00007f709a2b87f0 PC Speaker
00:00:03.615 R3 Write Ports: 0x61-0x62 00007f709a2b87f0 PC Speaker
00:00:03.615 !!
00:00:03.615 !! {mmio, <NULL>}
00:00:03.615 !!
00:00:03.615 MMIO ranges (pVM=00007f70a47b0000)
00:00:03.615 GC Phys Range                     pDevIns          Read             Write            Fill             pvUser           Description
00:00:03.615 00000000000a0000-00000000000bffff 00007f7097d37000 00007f70987a7ef0 00007f70987a7440 00007f70987a5cb0 0000000000000000 VGA - VGA Video Buffer
00:00:03.615                                R0 00007f7097d37000 ffffffffa0c06d10 ffffffffa0c074c0 ffffffffa0c06260 0000000000000000
00:00:03.615                                RC ff7fe000 ff7ea860 ff7ea480 ff7eaac0 00000000
00:00:03.615 00000000f0000000-00000000f001ffff 00007f709a2c02a0 00007f7098776be0 00007f7098776210 0000000000000000 0000000000000000 E1000
00:00:03.615                                R0 00007f709a2c02a0 ffffffffa0c0e050 ffffffffa0c0d770 0000000000000000 0000000000000000
00:00:03.615                                RC fe8452a0 ff7f1b30 ff7f1260 00000000 00000000
00:00:03.616 00000000fec00000-00000000fec00fff 00007f709a2b80e0 00007f709852bcf0 00007f709852be80 0000000000000000 00007f709a2b81a0 I/O APIC Memory
00:00:03.616                                R0 00007f709a2b80e0 ffffffffa0c16790 ffffffffa0c168b0 0000000000000000 0000000000000000
00:00:03.616                                RC fe83d0e0 ff7fa360 ff7fa480 00000000 00000000
00:00:03.616 00000000fee00000-00000000fee00fff 00007f709a2b7bb0 00007f709852d660 00007f709852e1c0 0000000000000000 00007f709a2b7c70 APIC Memory
00:00:03.616                                R0 00007f709a2b7bb0 ffffffffa0c17120 ffffffffa0c17ac0 0000000000000000 0000000000000000
00:00:03.616                                RC fe83cbb0 ff7fada0 ff7fb6d0 00000000 00000000
00:00:03.616 !!
00:00:03.616 !! {phys, <NULL>}
00:00:03.616 !!
00:00:03.616 RAM ranges (pVM=00007f70a47b0000)
00:00:03.616 GC Phys Range                     pvHC            
00:00:03.616 0000000000000000-00000000bb7fffff 0000000000000000 Base RAM
00:00:03.616 00000000e0000000-00000000e31fffff 00007f7094b37000 VRam
00:00:03.616 00000000f0000000-00000000f001ffff 0000000000000000 E1000
00:00:03.616 00000000f0400000-00000000f07fffff 00007f7097fd7000 VMMDev
00:00:03.616 00000000f0800000-00000000f0803fff 00007f7097fd3000 VMMDev Heap
00:00:03.616 00000000fec00000-00000000fec00fff 0000000000000000 I/O APIC Memory
00:00:03.616 00000000fee00000-00000000fee00fff 0000000000000000 APIC Memory
00:00:03.616 00000000ffff0000-00000000ffffffff 0000000000000000 PC BIOS - 0xffffffff
00:00:03.616 !!
00:00:03.616 !! {timers, <NULL>}
00:00:03.616 !!
00:00:03.616 Timers (pVM=00007f70a47b0000)
00:00:03.616 pTimerR3         offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:00:03.616 00007f709a2c7ae0 00000000 ffff7030 00000000 Real  000000000012933614 000000000012933631 2-ACTIVE                  EMT Yielder
00:00:03.616 00007f709a2c6f40 00000000 ffff1bf0 00000000 Virt  000000002608441173 000001199864031601 2-ACTIVE                  ACPI Timer
00:00:03.616 00007f709a2c54d0 00000000 00000000 00000000 Virt  000000002638402254 000000002636367750 2-ACTIVE                  Audio timer
00:00:03.616 00007f709a2c5450 00000000 00000000 00000000 Virt  000000002638402254 000000000000000000 1-STOPPED                 E1000 Link Up Timer
00:00:03.616 00007f709a2c53d0 00000000 00000000 00000000 Virt  000000002638402254 000000000000000000 1-STOPPED                 E1000 Late Interrupt Timer
00:00:03.616 00007f709a2bec50 00000000 00000000 00000000 Virt  000000002638402254 000000000000000000 1-STOPPED                 FDC Timer
00:00:03.616 00007f709a2beb10 00008fd0 00000000 00000000 Real  000000000012933614 000000000012933618 2-ACTIVE                  VGA Refresh Timer
00:00:03.616 00007f709a2b8bb0 00000000 00000000 00000000 Virt  000000002608441173 000000001990244140 1-STOPPED                 MC146818 RTC/CMOS - Second2
00:00:03.616 00007f709a2b8b30 0000e410 fffffb30 00000000 Virt  000000002608441173 000000002990000000 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:03.616 00007f709a2b8ab0 00000000 00000000 00000000 Virt  000000002608441173 000000000000000000 1-STOPPED                 MC146818 RTC/CMOS - Periodic
00:00:03.616 00007f709a2b8660 000004d0 00000000 00000000 Virt  000000002608441173 000000002663366574 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:03.616 00007f709a2b8060 00000000 00000000 00000000 Virt  000000002608441173 000000000000000000 1-STOPPED                 APIC Timer #0
00:00:03.616 !!
00:00:03.616 !! {activetimers, <NULL>}
00:00:03.616 !!
00:00:03.616 Active Timers (pVM=00007f70a47b0000)
00:00:03.616 pTimerR3         offNext  offPrev  offSched Clock Time               Expire             State                     Description
00:00:03.616 00007f709a2beb10 00008fd0 00000000 00000000 Real  000000000012933614 000000000012933618 2-ACTIVE                  VGA Refresh Timer
00:00:03.616 00007f709a2c7ae0 00000000 ffff7030 00000000 Real  000000000012933614 000000000012933631 2-ACTIVE                  EMT Yielder
00:00:03.616 00007f709a2c54d0 00000000 00000000 00000000 Virt  000000002638402254 000000002636367750 2-ACTIVE                  Audio timer
00:00:03.616 00007f709a2b8660 000004d0 00000000 00000000 VrSy  000000002608441173 000000002663366574 2-ACTIVE                  i8254 Programmable Interval Timer
00:00:03.616 00007f709a2b8b30 0000e410 fffffb30 00000000 VrSy  000000002608441173 000000002990000000 2-ACTIVE                  MC146818 RTC/CMOS - Second
00:00:03.616 00007f709a2c6f40 00000000 ffff1bf0 00000000 VrSy  000000002608441173 000001199864031601 2-ACTIVE                  ACPI Timer
00:00:03.616 !!
00:00:03.616 !! {handlers, phys virt hyper stats}
00:00:03.616 !!
00:00:03.616 Physical handlers: (PhysHandlers=63040 (0xf640))
00:00:03.616 From     - To (incl) HandlerHC UserHC    HandlerGC UserGC    Type     Description
00:00:03.616 00000000000a0000 - 00000000000bffff  00007f709fd92980  00007f709a2be6f0  ff79f8b0  fe8436f0  MMIO     VGA - VGA Video Buffer
00:00:03.616 00000000000c0000 - 00000000000c8fff  00007f709fd4d440  00007f709a2be8d0  ff7bac20  fe8438d0  Write    VGA BIOS
00:00:03.616 00000000000e0000 - 00000000000e0fff  00007f709fd4d440  00007f709a2c6910  ff7bac20  fe84b910  Write    ACPI RSDP
00:00:03.616 00000000000e1000 - 00000000000e1fff  00007f709fd4d440  00007f709a2b54f0  ff7bac20  fe83a4f0  Write    DMI tables
00:00:03.616 00000000000e2000 - 00000000000e6fff  00007f709fd4d440  00007f709a2b5df0  ff7bac20  fe83adf0  All      Net Boot ROM
00:00:03.616 00000000000f0000 - 00000000000fffff  00007f709fd4d440  00007f709a2b55f0  ff7bac20  fe83a5f0  Write    PC BIOS - 0xfffff
00:00:03.616 00000000e0000000 - 00000000e31fffff  00007f70987a6b40  00007f7097d370c0  ff7eb340  ff7fe0c0  Write    VGA LFB
00:00:03.616 00000000f0000000 - 00000000f001ffff  00007f709fd92980  00007f709a2c7250  ff79f8b0  fe84c250  MMIO     E1000
00:00:03.616 00000000fec00000 - 00000000fec00fff  00007f709fd92980  00007f709a2b82a0  ff79f8b0  fe83d2a0  MMIO     I/O APIC Memory
00:00:03.616 00000000fee00000 - 00000000fee00fff  00007f709fd92980  00007f709a2b7ed0  ff79f8b0  fe83ced0  MMIO     APIC Memory
00:00:03.616 00000000ffff0000 - 00000000ffffffff  00007f709fd4d440  00007f709a2b5940  ff7bac20  fe83a940  Write    PC BIOS - 0xffffffff
00:00:03.616 Virtual handlers:
00:00:03.616 From     - To (excl) HandlerHC HandlerGC Type     Description
00:00:03.616 Hypervisor Virtual handlers:
00:00:03.616 From     - To (excl) HandlerHC HandlerGC Type     Description
00:00:03.616 00000000fe808190 - 00000000fe80898f  0000000000000000  ff795a20  WriteHyp   Shadow IDT write access handler
00:00:03.616 00000000fe8096b0 - 00000000fe809737  0000000000000000  ff795300  WriteHyp   Shadow TSS write access handler
00:00:03.616 00000000ff56a000 - 00000000ff579fff  0000000000000000  ff795420  WriteHyp   Shadow GDT write access handler
00:00:03.616 00000000ff57b000 - 00000000ff58bfff  0000000000000000  ff795390  WriteHyp   Shadow LDT write access handler
00:00:03.616 !!
00:00:03.616 !! {cfgm, <NULL>}
00:00:03.616 !!
00:00:03.616 pRoot=0000000002222e40:{/}
00:00:03.616 [/] (level 0)
00:00:03.616   Name               <string>  = "Lucid" (cch=6)
00:00:03.616   UUID               <bytes>   = "9c 91 1a d6 fa 8a 8f 4f b5 e1 c3 12 6d 36 5f 92" (cb=16)
00:00:03.616   RamSize            <integer> = 0x00000000bb800000 (3145728000)
00:00:03.616   RamHoleSize        <integer> = 0x0000000020000000 (536870912)
00:00:03.616   NumCPUs            <integer> = 0x0000000000000001 (1)
00:00:03.616   TimerMillies       <integer> = 0x000000000000000a (10)
00:00:03.616   RawR3Enabled       <integer> = 0x0000000000000001 (1)
00:00:03.616   RawR0Enabled       <integer> = 0x0000000000000001 (1)
00:00:03.616   PATMEnabled        <integer> = 0x0000000000000001 (1)
00:00:03.616   CSAMEnabled        <integer> = 0x0000000000000001 (1)
00:00:03.616   HwVirtExtForced    <integer> = 0x0000000000000000 (0)
00:00:03.616   EnableNestedPaging <integer> = 0x0000000000000000 (0)
00:00:03.616   EnableVPID         <integer> = 0x0000000000000000 (0)
00:00:03.616   EnablePAE          <integer> = 0x0000000000000000 (0)
00:00:03.616 
00:00:03.616 [/HWVirtExt/] (level 1)
00:00:03.616 
00:00:03.616 [/PDM/] (level 1)
00:00:03.616 
00:00:03.616 [/PDM/Drivers/] (level 2)
00:00:03.616 
00:00:03.616 [/PDM/Drivers/VBoxC/] (level 3)
00:00:03.616   Path <string>  = "/usr/lib/virtualbox/components/VBoxC" (cch=37)
00:00:03.616 
00:00:03.616 [/Devices/] (level 1)
00:00:03.616 
00:00:03.616 [/Devices/pcarch/] (level 2)
00:00:03.616 
00:00:03.616 [/Devices/pcarch/0/] (level 3)
00:00:03.616   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.616 
00:00:03.616 [/Devices/pcarch/0/Config/] (level 4) (restricted root)
00:00:03.616 
00:00:03.616 [/Devices/pcbios/] (level 2)
00:00:03.616 
00:00:03.616 [/Devices/pcbios/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/pcbios/0/Config/] (level 4) (restricted root)
00:00:03.617   RamSize        <integer> = 0x00000000bb800000 (3145728000)
00:00:03.617   RamHoleSize    <integer> = 0x0000000020000000 (536870912)
00:00:03.617   NumCPUs        <integer> = 0x0000000000000001 (1)
00:00:03.617   HardDiskDevice <string>  = "piix3ide" (cch=9)
00:00:03.617   FloppyDevice   <string>  = "i82078" (cch=7)
00:00:03.617   IOAPIC         <integer> = 0x0000000000000001 (1)
00:00:03.617   PXEDebug       <integer> = 0x0000000000000000 (0)
00:00:03.617   UUID           <bytes>   = "9c 91 1a d6 fa 8a 8f 4f b5 e1 c3 12 6d 36 5f 92" (cb=16)
00:00:03.617   BootDevice0    <string>  = "IDE" (cch=4)
00:00:03.617   BootDevice1    <string>  = "DVD" (cch=4)
00:00:03.617   BootDevice2    <string>  = "NONE" (cch=5)
00:00:03.617   BootDevice3    <string>  = "NONE" (cch=5)
00:00:03.617 
00:00:03.617 [/Devices/8237A/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/8237A/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/8237A/0/Config/] (level 4) (restricted root)
00:00:03.617 
00:00:03.617 [/Devices/pci/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/pci/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/pci/0/Config/] (level 4) (restricted root)
00:00:03.617   IOAPIC <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/Config/] (level 4) (restricted root)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#0/] (level 4)
00:00:03.617   Driver <string>  = "KeyboardQueue" (cch=14)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.617   QueueSize <integer> = 0x0000000000000040 (64)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.617   Driver <string>  = "MainKeyboard" (cch=13)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
00:00:03.617   Object <integer> = 0x00000000021e0530 (35521840)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#1/] (level 4)
00:00:03.617   Driver <string>  = "MouseQueue" (cch=11)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#1/Config/] (level 5) (restricted root)
00:00:03.617   QueueSize <integer> = 0x0000000000000080 (128)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#1/AttachedDriver/] (level 5)
00:00:03.617   Driver <string>  = "MainMouse" (cch=10)
00:00:03.617 
00:00:03.617 [/Devices/pckbd/0/LUN#1/AttachedDriver/Config/] (level 6) (restricted root)
00:00:03.617   Object <integer> = 0x00000000021e0680 (35522176)
00:00:03.617 
00:00:03.617 [/Devices/i82078/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/Config/] (level 4) (restricted root)
00:00:03.617   IRQ       <integer> = 0x0000000000000006 (6)
00:00:03.617   DMA       <integer> = 0x0000000000000002 (2)
00:00:03.617   MemMapped <integer> = 0x0000000000000000 (0)
00:00:03.617   IOBase    <integer> = 0x00000000000003f0 (1008)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/LUN#999/] (level 4)
00:00:03.617   Driver <string>  = "MainStatus" (cch=11)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/LUN#999/Config/] (level 5) (restricted root)
00:00:03.617   papLeds <integer> = 0x00000000021dfbe0 (35519456)
00:00:03.617   First   <integer> = 0x0000000000000000 (0)
00:00:03.617   Last    <integer> = 0x0000000000000000 (0)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/LUN#0/] (level 4)
00:00:03.617   Driver <string>  = "Block" (cch=6)
00:00:03.617 
00:00:03.617 [/Devices/i82078/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.617   Type      <string>  = "Floppy 1.44" (cch=12)
00:00:03.617   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/acpi/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/acpi/0/] (level 3)
00:00:03.617   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.617   PCIDeviceNo   <integer> = 0x0000000000000007 (7)
00:00:03.617   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.617 
00:00:03.617 [/Devices/acpi/0/Config/] (level 4) (restricted root)
00:00:03.617   RamSize     <integer> = 0x00000000bb800000 (3145728000)
00:00:03.617   RamHoleSize <integer> = 0x0000000020000000 (536870912)
00:00:03.617   NumCPUs     <integer> = 0x0000000000000001 (1)
00:00:03.617   IOAPIC      <integer> = 0x0000000000000001 (1)
00:00:03.617   FdcEnabled  <integer> = 0x0000000000000001 (1)
00:00:03.617   ShowRtc     <integer> = 0x0000000000000000 (0)
00:00:03.617   ShowCpu     <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.617 [/Devices/acpi/0/LUN#0/] (level 4)
00:00:03.617   Driver <string>  = "ACPIHost" (cch=9)
00:00:03.617 
00:00:03.617 [/Devices/acpi/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.617 
00:00:03.617 [/Devices/i8254/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/i8254/0/] (level 3)
00:00:03.617 
00:00:03.617 [/Devices/i8254/0/Config/] (level 4) (restricted root)
00:00:03.617 
00:00:03.617 [/Devices/i8259/] (level 2)
00:00:03.617 
00:00:03.617 [/Devices/i8259/0/] (level 3)
00:00:03.617   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.617 
00:00:03.618 [/Devices/i8259/0/Config/] (level 4) (restricted root)
00:00:03.618 
00:00:03.618 [/Devices/apic/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/apic/0/] (level 3)
00:00:03.618   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.618 
00:00:03.618 [/Devices/apic/0/Config/] (level 4) (restricted root)
00:00:03.618   IOAPIC  <integer> = 0x0000000000000001 (1)
00:00:03.618   NumCPUs <integer> = 0x0000000000000001 (1)
00:00:03.618 
00:00:03.618 [/Devices/ioapic/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/ioapic/0/] (level 3)
00:00:03.618   Trusted <integer> = 0x0000000000000001 (1)
00:00:03.618 
00:00:03.618 [/Devices/ioapic/0/Config/] (level 4) (restricted root)
00:00:03.618 
00:00:03.618 [/Devices/mc146818/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/mc146818/0/] (level 3)
00:00:03.618 
00:00:03.618 [/Devices/mc146818/0/Config/] (level 4) (restricted root)
00:00:03.618 
00:00:03.618 [/Devices/vga/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/vga/0/] (level 3)
00:00:03.618   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.618   PCIDeviceNo   <integer> = 0x0000000000000002 (2)
00:00:03.618   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.618 
00:00:03.618 [/Devices/vga/0/Config/] (level 4) (restricted root)
00:00:03.618   VRamSize         <integer> = 0x0000000003200000 (52428800)
00:00:03.618   FadeIn           <integer> = 0x0000000000000001 (1)
00:00:03.618   FadeOut          <integer> = 0x0000000000000001 (1)
00:00:03.618   LogoTime         <integer> = 0x0000000000000000 (0)
00:00:03.618   LogoFile         <string>  = "" (cch=1)
00:00:03.618   ShowBootMenu     <integer> = 0x0000000000000002 (2)
00:00:03.618   CustomVideoModes <integer> = 0x0000000000000000 (0)
00:00:03.618   HeightReduction  <integer> = 0x0000000000000000 (0)
00:00:03.618 
00:00:03.618 [/Devices/vga/0/LUN#0/] (level 4)
00:00:03.618   Driver <string>  = "MainDisplay" (cch=12)
00:00:03.618 
00:00:03.618 [/Devices/vga/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.618   Object <integer> = 0x00000000021e07d0 (35522512)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/] (level 3)
00:00:03.618   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.618   PCIDeviceNo   <integer> = 0x0000000000000001 (1)
00:00:03.618   PCIFunctionNo <integer> = 0x0000000000000001 (1)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/Config/] (level 4) (restricted root)
00:00:03.618   Type <string>  = "PIIX4" (cch=6)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#999/] (level 4)
00:00:03.618   Driver <string>  = "MainStatus" (cch=11)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#999/Config/] (level 5) (restricted root)
00:00:03.618   papLeds <integer> = 0x00000000021dfbf0 (35519472)
00:00:03.618   First   <integer> = 0x0000000000000000 (0)
00:00:03.618   Last    <integer> = 0x0000000000000003 (3)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#2/] (level 4)
00:00:03.618   Driver <string>  = "Block" (cch=6)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#2/Config/] (level 5) (restricted root)
00:00:03.618   Type      <string>  = "DVD" (cch=4)
00:00:03.618   Mountable <integer> = 0x0000000000000001 (1)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#0/] (level 4)
00:00:03.618   Driver <string>  = "Block" (cch=6)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.618   Type      <string>  = "HardDisk" (cch=9)
00:00:03.618   Mountable <integer> = 0x0000000000000000 (0)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#0/AttachedDriver/] (level 5)
00:00:03.618   Driver <string>  = "VD" (cch=3)
00:00:03.618 
00:00:03.618 [/Devices/piix3ide/0/LUN#0/AttachedDriver/Config/] (level 6) (restricted root)
00:00:03.618   Path   <string>  = "/home/nick/.VirtualBox/Machines/lucid/lucid.vdi" (cch=48)
00:00:03.618   Format <string>  = "VDI" (cch=4)
00:00:03.618 
00:00:03.618 [/Devices/pcnet/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/e1000/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/] (level 3)
00:00:03.618   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.618   PCIDeviceNo   <integer> = 0x0000000000000003 (3)
00:00:03.618   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/Config/] (level 4) (restricted root)
00:00:03.618   AdapterType    <integer> = 0x0000000000000000 (0)
00:00:03.618   MAC            <bytes>   = "08 00 27 29 c0 0b" (cb=6)
00:00:03.618   CableConnected <integer> = 0x0000000000000001 (1)
00:00:03.618   LineSpeed      <integer> = 0x0000000000000000 (0)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/LUN#999/] (level 4)
00:00:03.618   Driver <string>  = "MainStatus" (cch=11)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/LUN#999/Config/] (level 5) (restricted root)
00:00:03.618   papLeds <integer> = 0x00000000021dfd80 (35519872)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/LUN#0/] (level 4)
00:00:03.618   Driver <string>  = "NAT" (cch=4)
00:00:03.618 
00:00:03.618 [/Devices/e1000/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.618   TFTPPrefix <string>  = "/home/nick/.VirtualBox/TFTP" (cch=28)
00:00:03.618   BootFile   <string>  = "Lucid.pxe" (cch=10)
00:00:03.618 
00:00:03.618 [/Devices/serial/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/parallel/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/VMMDev/] (level 2)
00:00:03.618 
00:00:03.618 [/Devices/VMMDev/0/] (level 3)
00:00:03.618   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.618   PCIDeviceNo   <integer> = 0x0000000000000004 (4)
00:00:03.619   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.619 
00:00:03.619 [/Devices/VMMDev/0/Config/] (level 4) (restricted root)
00:00:03.619 
00:00:03.619 [/Devices/VMMDev/0/LUN#0/] (level 4)
00:00:03.619   Driver <string>  = "MainVMMDev" (cch=11)
00:00:03.619 
00:00:03.619 [/Devices/VMMDev/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.619   Object <integer> = 0x00000000021e0060 (35520608)
00:00:03.619 
00:00:03.619 [/Devices/VMMDev/0/LUN#999/] (level 4)
00:00:03.619   Driver <string>  = "MainStatus" (cch=11)
00:00:03.619 
00:00:03.619 [/Devices/VMMDev/0/LUN#999/Config/] (level 5) (restricted root)
00:00:03.619   papLeds <integer> = 0x00000000021dfdc0 (35519936)
00:00:03.619   First   <integer> = 0x0000000000000000 (0)
00:00:03.619   Last    <integer> = 0x0000000000000000 (0)
00:00:03.619 
00:00:03.619 [/Devices/AudioSniffer/] (level 2)
00:00:03.619 
00:00:03.619 [/Devices/AudioSniffer/0/] (level 3)
00:00:03.619 
00:00:03.619 [/Devices/AudioSniffer/0/Config/] (level 4) (restricted root)
00:00:03.619 
00:00:03.619 [/Devices/AudioSniffer/0/LUN#0/] (level 4)
00:00:03.619   Driver <string>  = "MainAudioSniffer" (cch=17)
00:00:03.619 
00:00:03.619 [/Devices/AudioSniffer/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.619   Object <integer> = 0x00000000021dff30 (35520304)
00:00:03.619 
00:00:03.619 [/Devices/ichac97/] (level 2)
00:00:03.619 
00:00:03.619 [/Devices/ichac97/0/] (level 3)
00:00:03.619   Trusted       <integer> = 0x0000000000000001 (1)
00:00:03.619   PCIDeviceNo   <integer> = 0x0000000000000005 (5)
00:00:03.619   PCIFunctionNo <integer> = 0x0000000000000000 (0)
00:00:03.619 
00:00:03.619 [/Devices/ichac97/0/Config/] (level 4) (restricted root)
00:00:03.619 
00:00:03.619 [/Devices/ichac97/0/LUN#0/] (level 4)
00:00:03.619   Driver <string>  = "AUDIO" (cch=6)
00:00:03.619 
00:00:03.619 [/Devices/ichac97/0/LUN#0/Config/] (level 5) (restricted root)
00:00:03.619   AudioDriver <string>  = "pulse" (cch=6)
00:00:03.619   StreamName  <string>  = "Lucid" (cch=6)
00:00:03.619 
00:00:03.619 [/TM/] (level 1)
00:00:03.619   UTCOffset <integer> = 0x0000000000000000 (0)
00:00:03.619 
00:00:03.619 [/MM/] (level 1)
00:00:03.619 
00:00:03.619 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:00:04.620 Changing the VM state from 'RUNNING' to 'GURU_MEDITATION'.
00:00:19.166 Console::powerDown(): A request to power off the VM has been issued (mMachineState=8, InUninit=0)
00:00:19.177 Changing the VM state from 'GURU_MEDITATION' to 'OFF'.
00:00:19.178 Changing the VM state from 'OFF' to 'DESTROYING'.
00:00:19.178 ************************* Statistics *************************
00:00:19.178 /Devices/ATA0/Unit0/AtapiDMA            0 times
00:00:19.178 /Devices/ATA0/Unit0/AtapiPIO            0 times
00:00:19.178 /Devices/ATA0/Unit0/DMA                 0 times
00:00:19.178 /Devices/ATA0/Unit0/PIO                 4 times
00:00:19.178 /Devices/ATA0/Unit0/ReadBytes       27648 bytes
00:00:19.178 /Devices/ATA0/Unit0/WrittenBytes        0 bytes
00:00:19.178 /Devices/ATA0/Unit1/AtapiDMA            0 times
00:00:19.179 /Devices/ATA0/Unit1/AtapiPIO            0 times
00:00:19.179 /Devices/ATA0/Unit1/DMA                 0 times
00:00:19.179 /Devices/ATA0/Unit1/PIO                 0 times
00:00:19.179 /Devices/ATA0/Unit1/ReadBytes           0 bytes
00:00:19.179 /Devices/ATA0/Unit1/WrittenBytes        0 bytes
00:00:19.179 /Devices/ATA1/Unit0/AtapiDMA            0 times
00:00:19.179 /Devices/ATA1/Unit0/AtapiPIO            0 times
00:00:19.179 /Devices/ATA1/Unit0/DMA                 0 times
00:00:19.179 /Devices/ATA1/Unit0/PIO                 0 times
00:00:19.179 /Devices/ATA1/Unit0/ReadBytes           0 bytes
00:00:19.179 /Devices/ATA1/Unit0/WrittenBytes        0 bytes
00:00:19.179 /Devices/ATA1/Unit1/AtapiDMA            0 times
00:00:19.179 /Devices/ATA1/Unit1/AtapiPIO            0 times
00:00:19.179 /Devices/ATA1/Unit1/DMA                 0 times
00:00:19.179 /Devices/ATA1/Unit1/PIO                 0 times
00:00:19.179 /Devices/ATA1/Unit1/ReadBytes           0 bytes
00:00:19.179 /Devices/ATA1/Unit1/WrittenBytes        0 bytes
00:00:19.179 /Devices/E1k0/ReceiveBytes              0 bytes
00:00:19.179 /Devices/E1k0/TransmitBytes             0 bytes
00:00:19.179 /GVMM/EMTs                              1 calls
00:00:19.179 /GVMM/Sum/HaltBlocking                448 calls
00:00:19.179 /GVMM/Sum/HaltCalls                 14473 calls
00:00:19.179 /GVMM/Sum/HaltNotBlocking           14025 calls
00:00:19.179 /GVMM/Sum/HaltTimeouts                261 calls
00:00:19.179 /GVMM/Sum/HaltWakeUps                   0 calls
00:00:19.179 /GVMM/Sum/PokeCalls                     0 calls
00:00:19.179 /GVMM/Sum/PokeNotBusy                   0 calls
00:00:19.179 /GVMM/Sum/PollCalls                    38 calls
00:00:19.179 /GVMM/Sum/PollHalts                     0 calls
00:00:19.179 /GVMM/Sum/PollWakeUps                   0 calls
00:00:19.179 /GVMM/Sum/WakeUpCalls                 360 calls
00:00:19.179 /GVMM/Sum/WakeUpNotHalted             308 calls
00:00:19.179 /GVMM/Sum/WakeUpWakeUps                 0 calls
00:00:19.179 /GVMM/VM/HaltBlocking                 448 calls
00:00:19.179 /GVMM/VM/HaltCalls                  14473 calls
00:00:19.179 /GVMM/VM/HaltNotBlocking            14025 calls
00:00:19.179 /GVMM/VM/HaltTimeouts                 261 calls
00:00:19.179 /GVMM/VM/HaltWakeUps                    0 calls
00:00:19.179 /GVMM/VM/PokeCalls                      0 calls
00:00:19.179 /GVMM/VM/PokeNotBusy                    0 calls
00:00:19.179 /GVMM/VM/PollCalls                     38 calls
00:00:19.179 /GVMM/VM/PollHalts                      0 calls
00:00:19.179 /GVMM/VM/PollWakeUps                    0 calls
00:00:19.179 /GVMM/VM/WakeUpCalls                  360 calls
00:00:19.179 /GVMM/VM/WakeUpNotHalted              308 calls
00:00:19.179 /GVMM/VM/WakeUpWakeUps                  0 calls
00:00:19.179 /GVMM/VMs                               1 calls
00:00:19.179 /MM/HyperHeap/cbFree              1158544 bytes
00:00:19.179 /MM/HyperHeap/cbHeap              1310400 bytes
00:00:19.179 /PDM/CritSects/ATA0/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/ATA0/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/ATA0/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/ATA1/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/ATA1/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/ATA1/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/E1000#0/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/E1000#0/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/E1000#0/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/E1000#0RX/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/E1000#0RX/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/E1000#0RX/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/EM-REM/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/EM-REM/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/EM-REM/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/IOM EMT Lock/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/IOM EMT Lock/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/IOM EMT Lock/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/MM-HYPER/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/MM-HYPER/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/MM-HYPER/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/PDM/ContentionR3         0 times
00:00:19.179 /PDM/CritSects/PDM/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/PDM/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/PGM/ContentionR3         0 times
00:00:19.179 /PDM/CritSects/PGM/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/PGM/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/PS2KM#0/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/PS2KM#0/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/PS2KM#0/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/REM-Register/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/REM-Register/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/REM-Register/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/TM Timer Lock/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/TM Timer Lock/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/TM Timer Lock/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/TM VirtualSync Lock/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/TM VirtualSync Lock/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/TM VirtualSync Lock/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/VGA/ContentionR3         0 times
00:00:19.179 /PDM/CritSects/VGA/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/VGA/ContentionRZUnlock        0 times
00:00:19.179 /PDM/CritSects/VMMDev/ContentionR3        0 times
00:00:19.179 /PDM/CritSects/VMMDev/ContentionRZLock        0 times
00:00:19.179 /PDM/CritSects/VMMDev/ContentionRZUnlock        0 times
00:00:19.179 /PGM/CPU0/cGuestModeChanges            15 times
00:00:19.179 /PGM/ChunkR3Map/c                       2 times
00:00:19.179 /PGM/ChunkR3Map/cMax             4294967295 times
00:00:19.179 /PGM/Page/cAllPages                781926 times
00:00:19.179 /PGM/Page/cHandyPages                  28 times
00:00:19.179 /PGM/Page/cPrivatePages             14096 times
00:00:19.179 /PGM/Page/cSharedPages                  0 times
00:00:19.179 /PGM/Page/cZeroPages               767830 times
00:00:19.179 /PGM/cRelocations                       0 times
00:00:19.179 /PROF/CPU0/EM/ForcedActions           373 times
00:00:19.179 /PROF/CPU0/EM/Halted                  214 times
00:00:19.179 /PROF/CPU0/EM/RAWTotal                  0 times
00:00:19.179 /PROF/CPU0/EM/REMTotal                158 times
00:00:19.179 /PROF/CPU0/EM/Total              11517221222 ticks/call ( 11517221222 ticks,       1 times, max 11517221222, min 11517221222)
00:00:19.179 /PROF/VM/CPU0/Halt/Block           529762 ticks/call (  7657180185 ticks,   14454 times, max  45253506, min    2859)
00:00:19.179 /PROF/VM/CPU0/Halt/Timers            2928 ticks/call (    61532373 ticks,   21013 times, max    371669, min    2090)
00:00:19.179 /PROF/VM/CPU0/Halt/Yield             5548 ticks/call (      210829 ticks,      38 times, max      7695, min    5130)
00:00:19.179 /REM/TbFlushCount                       0 times
00:00:19.179 /REM/TbPhysInvldCount                   1 times
00:00:19.179 /REM/TlbFlushCount                     36 times
00:00:19.179 /TM/TSC/offCPU0                         0 ticks
00:00:19.179 /TM/VirtualSync/CurrentOffset        1172 ns
00:00:19.179 ********************* End of statistics **********************
00:00:19.192 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
```

i dont know if this is a bug with ubuntu or just a problem with how iv set up virtualbox please let me know

---

