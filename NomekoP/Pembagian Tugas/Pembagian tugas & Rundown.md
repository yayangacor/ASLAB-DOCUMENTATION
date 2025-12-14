## ⏰ STRUKTUR WAKTU (Minggu, mulai jam 09.00)

```
saat acq, kita bisa sambil hafalin trainee & trainer
-LISTING PROGRESS DI EXCEL JAM 14:00, 16:00, 18:00!!! 

07.00 - 09.00 Pembagian kelompok
09.00 - 13.00 Ngerjain BP per kelompok sambil acq (4 jam)
1 jam Riset
2 jam diskusi dalam sub-group
1 jam dokumentasi hasil

13.00 - 13.30 Break Istirahat
13.30 -  15.00  Pemerataan  1

15.00 - 19.00 Ngerjain BP per kelompok sambil acq
1 jam Riset
2 jam diskusi dalam sub-group
1 jam dokumentasi hasil

19.00 - 20.00 Break Istirahat
20.00 - 22.00 Pemerataan 2

22.00 - 00.00 Pendalaman subco, materi & persiapan present besok
```

---

## 👥 PEMBAGIAN KELOMPOK & TOPIK

Berdasarkan goals yang kamu sebutkan, saya kelompokkan berdasarkan **keterkaitan konsep**:

### **35 Anggota → 6 Sub-Groups**

| Sub-Group | Jumlah  | Topik Utama                     | Tingkat Kesulitan |
| --------- | ------- | ------------------------------- | ----------------- |
| **A**     | 6 orang | **Parsing Map**                 | 🔴 Tinggi         |
| **B**     | 6 orang | **OOP + JDBC + Database SQL**   | 🔴 Tinggi         |
| **C**     | 6 orang | **Movement Player + Minimap**   | 🟡 Sedang         |
| **D**     | 6 orang | **Shop + Backpack**             | 🟡 Sedang         |
| **E**     | 6 orang | **Landing Page + Profile Page** | 🟢 Dasar          |
| **F**     | 5 orang | **Progress Bar + BGM & SFX**    | 🟢 Dasar          |

---

## 📚 DETAIL MATERI RISET & DISKUSI PER KELOMPOK

---

### **🔴 SUB-GROUP A: PARSING MAP**

**(Tim dengan kemampuan tinggi)**

#### Topik yang Harus Dipahami:

```
1. KONSEP DASAR TILEMAP
   ├── Apa itu tilemap dan tileset?
   ├── Bagaimana game 2D menggunakan grid-based map?
   ├── Ukuran chunk (16x16 pixel) dan kenapa dipilih ukuran itu?
   └── Konsep layer dalam map (ground, collision, objects)

2. PARSING CSV
   ├── Bagaimana membaca file CSV di Java?
   ├── Struktur walkable_grid.csv (0 = tidak bisa dilewati, 1 = bisa)
   ├── Struktur terrain_type_grid.csv (bush, openWater, pokemonCenter, dll)
   └── Mapping koordinat CSV ke koordinat tilemap

3. FORMULA KONVERSI ID KE KOORDINAT
   ├── Tilemap 75 chunk (width) x 32 chunk (height)
   ├── Formula unflatten:
   │   x = id % width (contoh: 1215 % 75 = 15)
   │   y = id / width (contoh: 1215 / 75 = 16)
   └── Contoh praktis dengan beberapa ID

4. RENDERING MAP
   ├── Konsep viewport/camera (hanya render yang terlihat)
   ├── Bagaimana menggambar tile berdasarkan koordinat?
   └── Kapan map harus berganti (edge transition)

5. TERRAIN INTERACTION
   ├── Tile walkable vs non-walkable
   ├── Special tiles: bush (10% encounter), water (perlu surf)
   ├── Building tiles: pokemonCenter, gym, home, profHouse
   └── Logic ketika player step on tile tertentu
```

#### Pertanyaan Diskusi:

1. Bagaimana cara efisien menyimpan data 75x32 tiles di memory?
2. Apa yang terjadi ketika player berdiri di edge tile?
3. Bagaimana membedakan tile yang sama secara visual tapi berbeda fungsi?
4. Bagaimana implementasi 10% chance encounter di bush/water?

#### Output Dokumentasi:

- Diagram visual proses parsing CSV → Tile Object → Render
- Pseudocode/flowchart untuk map loading
- Contoh perhitungan manual id → coordinate

---

### **🔴 SUB-GROUP B: OOP + JDBC + DATABASE SQL**

#### Topik yang Harus Dipahami:

```
1. KONSEP OOP UNTUK GAME
   ├── Class dan Object dalam konteks Pokemon game
   │   ├── Pokemon sebagai class (attributes: hp, attack, type, dll)
   │   ├── Item sebagai abstract class (HealItem, PokeballItem, HMItem)
   │   └── Trainer, Location, Badge sebagai class
   ├── Inheritance (pewarisan)
   │   └── Contoh: HealItem extends Item
   ├── Encapsulation
   │   └── Private attributes + getter/setter
   ├── Polymorphism
   │   └── Contoh: berbagai jenis Item dengan method use() berbeda
   └── Abstraction
       └── Abstract class untuk entity umum

2. KONSEP JDBC
   ├── Apa itu JDBC dan fungsinya?
   ├── Connection string format:
   │   jdbc:mysql://localhost:3306/nomekop
   ├── Steps koneksi:
   │   1. Load driver
   │   2. Create connection
   │   3. Create statement
   │   4. Execute query
   │   5. Process result
   │   6. Close connection
   └── Singleton pattern untuk DatabaseConnection

3. STRUKTUR DATABASE NOMEKOP
   ├── Tabel READ-ONLY (data game):
   │   ├── pokemon (semua data Pokemon)
   │   ├── pokemonskill (semua skill)
   │   ├── pokemonskillheader (relasi pokemon-skill)
   │   ├── item, healitem, pokeballitem, hmitem
   │   ├── trainer, trainerpokemon
   │   ├── location, badge, locationbadgeheader
   │   └── Relasi antar tabel
   │
   └── Tabel READ-WRITE (data player):
       ├── usersave (username, password, balance, saveLoc)
       ├── userpokemon (pokemon milik player)
       ├── useritem (inventory player)
       ├── userbadge (badge yang sudah didapat)
       ├── uservisitedlocation (lokasi yang pernah dikunjungi)
       └── defeatedtrainer (gym leader yang sudah dikalahkan)

4. DAO PATTERN
   ├── Apa itu Data Access Object?
   ├── Kenapa memisahkan logic database dari business logic?
   └── Contoh: PokemonDAO dengan method findByNumber(), findAll()
```

#### Pertanyaan Diskusi:

1. Bagaimana hubungan antara tabel `pokemon` dan `userpokemon`?
2. Kenapa `healitem`, `pokeballitem`, `hmitem` terpisah dari `item`?
3. Apa yang terjadi jika connection database gagal di Title Screen?
4. Bagaimana menyimpan state game ketika player exit?

#### Output Dokumentasi:

- Diagram class untuk entity utama (Pokemon, Item, Trainer)
- Flowchart koneksi JDBC
- Mapping tabel database ke Java class

---

### **🟡 SUB-GROUP C: MOVEMENT PLAYER + MINIMAP**

#### Topik yang Harus Dipahami:

```
1. PLAYER MOVEMENT
   ├── Input handling di JavaFX
   │   ├── KeyEvent untuk WASD atau Arrow keys
   │   └── Event listener pada Scene
   ├── Grid-based movement
   │   ├── Player bergerak per tile (bukan pixel)
   │   ├── Validasi sebelum bergerak:
   │   │   1. Cek tile tujuan walkable?
   │   │   2. Cek terrain type (water perlu surf)
   │   │   3. Cek edge map (trigger transition)
   │   └── Update posisi x, y player
   ├── Player sprite
   │   ├── 4 arah (up, down, left, right)
   │   ├── Walking animation frames
   │   └── Surfing sprite (berbeda)
   └── Collision detection
       └── Sebelum move, cek tile[newX][newY].isWalkable()

2. SPECIAL MOVEMENT: SURFING
   ├── Trigger: player mencoba step ke water tile
   ├── Validasi: cek apakah ada Pokemon dengan skill "Surf" di deck
   ├── Jika tidak ada → tampilkan pesan error
   ├── Jika ada → konfirmasi dialog "Do you want to surf?"
   ├── Change sprite ke surfing mode
   └── Sekarang player bisa jalan di water tiles

3. MINIMAP SYSTEM
   ├── Konsep world map overview
   ├── Node locations (dari PDF):
   │   ├── C-Town (7, 8)
   │   ├── DB-Town (8, 5)
   │   ├── Java-Town (8, 3)
   │   ├── Web-Town (3, 4)
   │   ├── Network-Town (3, 9)
   │   └── Routes: 724, 600, Soft Skill, 611
   ├── Current location indicator
   ├── Visited vs unvisited locations
   └── Fly mechanic
       ├── Click on visited location
       ├── Validasi: ada Pokemon dengan skill "Fly" di deck?
       ├── Konfirmasi dialog
       └── Teleport player ke lokasi tersebut

4. MAP TRANSITION
   ├── Ketika player di edge tile
   ├── Detect arah keluar (north/south/east/west)
   ├── Load map baru berdasarkan koneksi antar lokasi
   └── Set posisi player di edge sebaliknya
```

#### Pertanyaan Diskusi:

1. Bagaimana mencegah player bergerak terlalu cepat (spam key)?
2. Apa yang terjadi jika player keluar dari air ke darat?
3. Bagaimana menyimpan lokasi yang sudah dikunjungi ke database?
4. Kenapa Fly hanya bisa ke lokasi yang pernah dikunjungi?

#### Output Dokumentasi:

- Flowchart movement validation
- Diagram state player (normal, surfing)
- Visual minimap dengan koordinat nodes

---

### **🟡 SUB-GROUP D: SHOP + BACKPACK**

#### Topik yang Harus Dipahami:

```
1. SHOP SYSTEM
   ├── Lokasi: di dalam Pokemon Center
   ├── UI Components:
   │   ├── TableView untuk daftar item
   │   ├── Tab/Menu untuk filter (Heal, Pokeball, HM)
   │   ├── Balance display (dari usersave.balance)
   │   ├── Item description panel
   │   └── Buy button + quantity slider
   ├── Data source:
   │   ├── Heal items dari JOIN item + healitem
   │   ├── Pokeball items dari JOIN item + pokeballitem
   │   └── HM items dari JOIN item + hmitem
   ├── Buy transaction:
   │   1. Validasi balance >= total price
   │   2. Kurangi balance di usersave
   │   3. Tambah/update item di useritem
   │   4. Update tampilan balance
   └── Edge cases:
       ├── Balance tidak cukup → disable buy button
       └── Item sudah punya → tambah quantity, bukan insert baru

2. BACKPACK SYSTEM
   ├── Akses: dari game map atau battle
   ├── UI Components:
   │   ├── TableView untuk inventory (nama, jumlah)
   │   ├── 3 tabs: Potions, Pokeball, TMs
   │   ├── Bag sprite berubah sesuai tab aktif
   │   ├── Item description + sprite
   │   └── Use button
   ├── Data source: useritem JOIN item
   ├── Filter berdasarkan itemType
   └── Use item flow:
       ├── Select item → Select Pokemon target
       ├── Apply effect:
       │   ├── HealItem: tambah HP dan/atau cleanse status
       │   ├── HM: ajarkan skill ke Pokemon
       │   └── Pokeball: hanya bisa di battle
       └── Kurangi quantity di useritem

3. ITEM TYPES & EFFECTS
   ├── HealItem attributes:
   │   ├── hpIncreaseFlat (contoh: Potion +20 HP)
   │   ├── hpIncreasePct (contoh: +50% max HP)
   │   └── cleanseStatus (contoh: Antidote → cure poison)
   ├── PokeballItem attributes:
   │   └── catchRate (decimal, mempengaruhi peluang tangkap)
   └── HMItem attributes:
       └── skillId (skill yang diajarkan, e.g., Surf, Fly)

4. RELASI SHOP-BACKPACK
   ├── Item dibeli di Shop → masuk Backpack
   ├── Item dipakai di Backpack → quantity berkurang
   └── Jika quantity = 0 → item hilang dari tampilan
```

#### Pertanyaan Diskusi:

1. Bagaimana menampilkan item yang berbeda tipe dalam satu TableView?
2. Apa validasi yang perlu dilakukan sebelum use item?
3. Bagaimana membedakan item yang bisa dipakai di luar battle vs di battle saja?
4. Bagaimana flow ketika HM diajarkan ke Pokemon yang sudah punya 4 skill?

#### Output Dokumentasi:

- Mockup/wireframe Shop screen dan Backpack screen
- Flowchart buy transaction
- Flowchart use item

---

### **🟢 SUB-GROUP E: LANDING PAGE + PROFILE PAGE**

#### Topik yang Harus Dipahami:

```
1. JAVAFX SCENE MANAGEMENT
   ├── Konsep Stage dan Scene
   ├── Controller class untuk logic
   ├── Switching antar scene
   └── CSS styling di JavaFX

2. TITLE SCREEN
   ├── Elements:
   │   ├── Game title "NomekoP IV Edition"
   │   ├── Background GIF (animated)
   │   ├── Pokemon sprite (static/animated)
   │   └── Text "Press Enter or Click the Screen" (blinking effect)
   ├── Interactions:
   │   ├── KeyEvent ENTER → navigate ke Landing Page
   │   ├── MouseClick → navigate ke Landing Page
   │   └── SEBELUM navigate: cek JDBC connection
   └── Error handling:
       └── Jika connection gagal → Alert error message

3. LANDING PAGE
   ├── Elements:
   │   ├── Background image
   │   └── 3 Buttons (vertical layout)
   ├── Button functions:
   │   ├── "Continue Game" → Load saved state, masuk game
   │   ├── "Start New Game" → Registration Page
   │   └── "Back to Title Screen" → Title Screen
   └── Validasi Continue:
       └── Cek apakah ada data di usersave

4. REGISTRATION PAGE (Multi-step)
   ├── Step 1: Username Input
   │   ├── Label "What's your NAME?"
   │   ├── TextField
   │   └── OK button → next step
   ├── Step 2: Password Input
   │   ├── Label "Now enter PASSWORD:"
   │   ├── PasswordField (masked *****)
   │   └── OK button → next step
   ├── Step 3: Detail Information
   │   ├── RadioButton group: Male / Female / Other
   │   ├── ComboBox untuk DOB (Year, Month, Day)
   │   ├── CheckBox "I agree to terms and conditions"
   │   └── OK button → save & go to Landing Page
   └── Save ke database:
       └── INSERT ke usersave (usn, pass, default values)

5. PROFILE PAGE
   ├── Akses dari Pause Menu
   ├── Display info dari usersave:
   │   ├── Username
   │   ├── Profile picture (jika ada)
   │   ├── Bio
   │   ├── Balance
   │   └── Current location (saveLoc)
   └── Edit functionality (optional)
```

#### Pertanyaan Diskusi:

1. Bagaimana membuat text blinking effect di JavaFX?
2. Bagaimana memastikan password tersimpan dengan aman?
3. Apa yang terjadi jika user klik Continue tapi belum ada save data?
4. Bagaimana flow navigation antar page di JavaFX?

#### Output Dokumentasi:

- Wireframe/mockup semua screen
- Flowchart navigation antar page
- List validasi yang diperlukan di setiap form

---

### **🟢 SUB-GROUP F: PROGRESS BAR + BGM & SFX**

#### Topik yang Harus Dipahami:

```
1. PROGRESS BAR CONCEPTS
   ├── HP Bar
   │   ├── Current HP / Max HP
   │   ├── Visual: bar yang berkurang
   │   ├── Color coding (hijau > kuning > merah)
   │   └── Smooth animation saat HP berubah
   ├── EXP Bar
   │   ├── Current EXP / EXP needed for next level
   │   ├── Reset ke 0 saat level up
   │   └── Visual feedback saat dapat EXP
   └── JavaFX ProgressBar component
       ├── setProgress(double value) → 0.0 to 1.0
       └── CSS styling untuk warna

2. HP BAR CALCULATION
   ├── Pokemon base HP dari database (pokemon.hp)
   ├── Current HP dari userpokemon.currentHp
   ├── Progress value = currentHp / maxHp
   └── Update saat:
       ├── Damage taken in battle
       ├── Healed by item/Pokemon Center
       └── Status effect damage (poison, burn)

3. EXP BAR CALCULATION
   ├── EXP formula (simplified):
   │   └── EXP needed = level^3 atau formula custom
   ├── EXP gain dari defeated Pokemon
   ├── Distributed ke semua Pokemon yang participate
   └── Level up trigger:
       └── currentExp >= expNeeded → level++, reset exp

4. BGM (BACKGROUND MUSIC)
   ├── JavaFX Media dan MediaPlayer
   ├── Audio format: MP3 atau WAV
   ├── BGM tracks needed:
   │   ├── intro (Title Screen)
   │   ├── town (saat di kota)
   │   ├── route (saat di route)
   │   ├── battle_wild (battle Pokemon liar)
   │   ├── battle_gym (battle Gym Leader)
   │   ├── pokemon_center (di Pokemon Center)
   │   ├── gym (di dalam Gym)
   │   ├── surf (saat surfing)
   │   ├── professor (di rumah Professor)
   │   └── evolution (saat evolusi)
   ├── BGM behavior:
   │   ├── Loop continuously
   │   ├── Stop previous BGM sebelum play baru
   │   └── Smooth transition (fade out/in) - optional
   └── AudioManager singleton pattern

5. SFX (SOUND EFFECTS)
   ├── Short audio clips, tidak loop
   ├── SFX categories:
   │   ├── Move types: fire, water, grass, electric, dll
   │   ├── Status effects: poison tick, freeze, burn
   │   ├── UI sounds: button click, menu open
   │   └── Battle: hit, critical, faint
   └── Play SFX without stopping BGM
       └── Separate MediaPlayer untuk SFX

6. AUDIO MANAGER DESIGN
   ├── Singleton class
   ├── Methods:
   │   ├── playBGM(String trackName)
   │   ├── stopBGM()
   │   ├── playSFX(String effectName)
   │   ├── setVolume(double level)
   │   └── mute() / unmute()
   └── Resource loading dari /resources/audio/
```

#### Pertanyaan Diskusi:

1. Bagaimana menghitung max HP Pokemon berdasarkan level?
2. Kapan HP bar harus berubah warna?
3. Bagaimana handle situasi BGM dan SFX playing bersamaan?
4. Bagaimana memastikan audio resource tidak memory leak?

#### Output Dokumentasi:

- Formula perhitungan HP dan EXP
- List semua BGM dan kapan dimainkan
- List semua SFX dan trigger-nya
- Diagram AudioManager class

---

## 📋 TEMPLATE DOKUMENTASI

Setiap kelompok wajib membuat dokumentasi dengan format:

```markdown
# DOKUMENTASI HASIL RISET
## Sub-Group: [A/B/C/D/E/F]
## Topik: [Nama Topik]
## Tanggal: [DD/MM/YYYY]
## Anggota:
1. [Nama]
2. [Nama]
...

---

## 1. RINGKASAN KONSEP
[Jelaskan konsep utama dengan bahasa sendiri]

## 2. POIN-POIN PENTING
- [Poin 1]
- [Poin 2]
- ...

## 3. DIAGRAM/VISUALISASI
[Gambar atau flowchart]

## 4. PERTANYAAN YANG TERJAWAB
- Q: [Pertanyaan]
  A: [Jawaban dari diskusi]

## 5. PERTANYAAN YANG BELUM TERJAWAB
- [Pertanyaan yang perlu riset lebih lanjut]

## 6. REKOMENDASI UNTUK IMPLEMENTASI
[Saran pendekatan ketika nanti mengerjakan]

## 7. SUMBER REFERENSI
- [Link video/artikel yang membantu]
```


---

## ✅ CHECKLIST KEBERHASILAN

Setiap kelompok dianggap berhasil jika:

- [ ] Semua anggota memahami konsep dasar topik mereka
- [ ] Dokumentasi tertulis lengkap
- [ ] Mampu menjelaskan ke kelompok lain saat pemerataan
- [ ] Menjawab minimal 3 pertanyaan diskusi
- [ ] Mengidentifikasi minimal 2 potensi kesulitan saat implementasi

---

