# Set Project Version and Language
project('rocdecode')

# project('rocdecode', default_options : ['default_library=static'])

libdrm_proj = subproject('drm', default_options: [
  'tests=false', 'amdgpu=enabled', 'intel=disabled', 'radeon=disabled', 'nouveau=disabled', 'vmwgfx=disabled'])
libdrm_dep = libdrm_proj.get_variable('ext_libdrm_amdgpu')

libva_proj = subproject('libva', default_options:[
  'default_library=static', 'with_glx=no', 'with_wayland=no', 'with_win32=no', 'with_x11=yes'
])
libva_dep = libva_proj.get_variable('libva_dep')

meson.override_dependency('libva', libva_dep)

mesa_proj = subproject('mesa', default_options:
  ['default_library=static', 'gallium-drivers=radeonsi', 'gallium-va=enabled',
   'gallium-vdpau=disabled', 'video-codecs=all', 'gbm=disabled', 'egl=disabled',
   'gles1=disabled', 'gles2=disabled', 'glx=disabled', 'glvnd=disabled',
   'opengl=false', 'vulkan-drivers=[]', 'platforms=[]', 'llvm=disabled', 'xmlconfig=disabled'])
