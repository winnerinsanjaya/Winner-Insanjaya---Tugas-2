# Winner-Insanjaya---Tugas-2
Tugas 2 Diklat 3-in-1 BDI Denpasar X Agate

----Bugs----
1. Variable _score yang tidak ada di GameManager.cs [Very High]
2. Variable score yang bertipe int di-assign kedalam text [Very High]
3. Game sudah berjalan bahkan sebelum tombol play ditekan [Very High]
4. Plane masih terjatuh setelah countdown berakhir [Very High]  
5. Plane malah lebih kebawah saat diklik [Very High]  
6. Plane masih melaju bahkan setelah menabrak Obstacle [High]
7. Plane tidak mati saat menabrak rintangan bawah [High]
8. Highscore belum berfungsi [Medium]

----Approach----

1. 
Mengubah variable _score --> score

3. 
Mengubah statement scoretext.text = score menjadi scoretext.text = score.ToString();

3. 
menambahkan CountdownText.OnCountdownFinished += OnCountdownFinished;
pada GameManager.cs di fungsi OnEnabled;
CountdownText.OnCountdownFinished += OnCountdownFinished;

4.
GameManager.cs Line 32:
change -> public bool GameOver { get { return !gameOver; } }
to -> public bool GameOver { get { return gameOver; } }
shingga dari awal kondisi akan tidak game over, begitu seterusnya

5.
tidak naik, bahkan turun karena pada :
TapController.cs Line 69, pada addforce malah Vector2.down.
seharusnya Vector2.up

6. 
pada TapController.cs Line 86, terjadi kesalahan pada penulisan tag:
if (col.gameObject.tag == "DeadZones") {
seharusnya:
if (col.gameObject.tag == "DeadZone") {

7. 
add tag ke prefabs woods. yang bawah

9.
GameManager.cs Line 62
if (score > savedScore) {
