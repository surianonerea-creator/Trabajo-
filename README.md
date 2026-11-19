-<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CINÉORA — Tu mundo de cine</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700&display=swap');

:root {
  --bg: #100d10;
  --panel: #1b151b;
  --panel2: #241b23;
  --pink: #d79aaa;
  --pink2: #f0bdca;
  --text: #f8eff2;
  --muted: #a99aa3;
  --line: #392b35;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
}

button, input, select, textarea { font: inherit; }
button { cursor: pointer; }

header {
  position: sticky;
  top: 0;
  z-index: 10;
  background: rgba(16,13,16,.94);
  backdrop-filter: blur(15px);
  border-bottom: 1px solid var(--line);
  padding: 17px 7%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

.logo {
  font-family: 'Playfair Display', serif;
  font-size: 29px;
  letter-spacing: 4px;
  color: var(--pink2);
}

.logo small {
  display: block;
  font-family: 'DM Sans', sans-serif;
  font-size: 9px;
  letter-spacing: 4px;
  color: var(--muted);
  text-align: center;
}

nav { display: flex; gap: 23px; }

nav a {
  color: var(--muted);
  text-decoration: none;
  font-size: 13px;
}

nav a:hover { color: var(--pink2); }

.hero {
  padding: 78px 7% 70px;
  min-height: 355px;
  background:
    linear-gradient(90deg, rgba(16,13,16,.98), rgba(16,13,16,.77), rgba(16,13,16,.2)),
    linear-gradient(135deg, #37232f, #161017 65%, #4a2939);
  display: flex;
  align-items: center;
}

.hero-content { max-width: 610px; }

.eyebrow {
  color: var(--pink);
  text-transform: uppercase;
  letter-spacing: 3px;
  font-size: 11px;
}

h1, h2, h3 {
  font-family: 'Playfair Display', serif;
  font-weight: 500;
}

h1 {
  font-size: clamp(43px, 7vw, 72px);
  line-height: 1.05;
  margin: 16px 0;
}

h1 em { color: var(--pink2); }

.hero p {
  color: #d2c4cb;
  line-height: 1.8;
  max-width: 470px;
}

.primary-btn, .secondary-btn {
  border: 0;
  border-radius: 5px;
  padding: 12px 19px;
  margin-top: 13px;
}

.primary-btn {
  background: var(--pink);
  color: #21151c;
  font-weight: 700;
}

.primary-btn:hover { background: var(--pink2); }

.secondary-btn {
  background: var(--panel2);
  color: var(--text);
  border: 1px solid var(--line);
}

main { padding: 38px 7% 70px; }

.section-heading {
  display: flex;
  justify-content: space-between;
  align-items: end;
  gap: 15px;
  margin-bottom: 22px;
}

.section-heading h2 {
  font-size: 30px;
  margin: 6px 0 0;
}

.muted { color: var(--muted); font-size: 13px; }

.controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 27px;
}

.controls input, .controls select,
.form-input, .form-textarea {
  background: var(--panel);
  color: var(--text);
  border: 1px solid var(--line);
  border-radius: 6px;
  padding: 12px 14px;
  outline: none;
}

.controls input { flex: 1; min-width: 180px; }

.controls select { min-width: 145px; }

input:focus, textarea:focus, select:focus {
  border-color: var(--pink);
}

.movie-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 25px 17px;
}

.movie-card { min-width: 0; }

.poster {
  height: 285px;
  width: 100%;
  position: relative;
  border-radius: 7px;
  overflow: hidden;
  cursor: pointer;
  background: linear-gradient(145deg, #523342, #17121b);
  transition: transform .2s;
}

.poster:hover { transform: translateY(-5px); }

.poster img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  display: block;
}

.poster-fallback {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  text-align: center;
  font-family: 'Playfair Display', serif;
  font-size: 27px;
  color: #f7d8e1;
  background: linear-gradient(145deg, #533044, #1b1420 70%);
}

.favorite {
  position: absolute;
  right: 10px;
  top: 10px;
  z-index: 2;
  border: 0;
  background: rgba(12,9,12,.8);
  color: white;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  font-size: 20px;
}

.favorite.active { color: #ff9eb9; }

.poster-label {
  position: absolute;
  left: 9px;
  bottom: 9px;
  background: rgba(15,10,15,.85);
  padding: 6px 9px;
  border-radius: 4px;
  font-size: 10px;
  color: var(--pink2);
  letter-spacing: 1px;
}

.movie-title {
  font-family: 'Playfair Display', serif;
  font-size: 18px;
  margin: 12px 0 5px;
}

.movie-meta { color: var(--muted); font-size: 12px; }

.rating-line {
  margin-top: 9px;
  color: var(--pink2);
  font-size: 13px;
}

.rating-line span { color: var(--muted); }

.review-section {
  margin-top: 75px;
  padding-top: 32px;
  border-top: 1px solid var(--line);
}

.review-layout {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(270px, .8fr);
  gap: 28px;
  align-items: start;
}

.panel {
  background: var(--panel);
  border: 1px solid var(--line);
  border-radius: 9px;
  padding: 22px;
}

.panel h3 { font-size: 23px; margin: 0 0 8px; }

.form-label {
  display: block;
  color: var(--muted);
  font-size: 12px;
  margin: 16px 0 7px;
}

.form-input, .form-textarea {
  width: 100%;
  display: block;
}

.form-textarea {
  min-height: 105px;
  resize: vertical;
}

.star-picker {
  display: flex;
  gap: 3px;
  margin-top: 4px;
}

.star {
  font-size: 31px;
  line-height: 1;
  color: #594653;
  cursor: pointer;
  user-select: none;
}

.star.selected { color: var(--pink2); }

.rating-hint {
  font-size: 12px;
  color: var(--pink);
  margin-top: 8px;
}

.review-card {
  border-bottom: 1px solid var(--line);
  padding: 18px 0;
}

.review-card:last-child { border-bottom: 0; }

.review-top {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.review-name { font-weight: 700; font-size: 14px; }

.review-date { color: var(--muted); font-size: 11px; margin-top: 4px; }

.review-stars { color: var(--pink2); letter-spacing: 1px; }

.review-text {
  color: #d9cdd3;
  font-size: 13px;
  line-height: 1.75;
  margin: 13px 0;
  overflow-wrap: anywhere;
}

.helpful {
  border: 1px solid var(--line);
  border-radius: 5px;
  color: var(--muted);
  background: transparent;
  padding: 7px 10px;
  font-size: 11px;
}

.helpful:hover { color: var(--pink2); }

.empty {
  padding: 25px 0;
  color: var(--muted);
  font-size: 13px;
}

footer {
  border-top: 1px solid var(--line);
  text-align: center;
  padding: 35px 7%;
  color: var(--muted);
  font-size: 12px;
  line-height: 1.8;
}

footer strong {
  display: block;
  font-family: 'Playfair Display', serif;
  letter-spacing: 4px;
  font-size: 21px;
  color: var(--pink2);
}

.notice {
  margin-top: 15px;
  color: var(--muted);
  font-size: 11px;
  line-height: 1.6;
}

@media (max-width: 950px) {
  .movie-grid { grid-template-columns: repeat(3, minmax(0, 1fr)); }
  .poster { height: 260px; }
}

@media (max-width: 650px) {
  header { padding: 15px 5%; flex-wrap: wrap; }
  nav { gap: 14px; }
  nav a { font-size: 12px; }
  .hero { padding: 55px 5%; }
  main { padding: 30px 5% 55px; }
  .movie-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 22px 12px; }
  .poster { height: 240px; }
  .review-layout { grid-template-columns: 1fr; }
  .logo { font-size: 24px; }
}

@media (max-width: 370px) {
  .poster { height: 200px; }
}
</style>
</head>

<body>

<header>
  <div class="logo">CINÉORA<small>EL ARTE DE SENTIR</small></div>
  <nav>
    <a href="#peliculas">Películas</a>
    <a href="#resenas">Reseñas</a>
    <a href="#favoritas" id="favoritesLink">♡ Favoritas</a>
  </nav>
</header>

<section class="hero">
  <div class="hero-content">
    <div class="eyebrow">Tu rincón cinematográfico</div>
    <h1>Hay historias que <em>se quedan.</em></h1>
    <p>
      Descubrí películas, compartí lo que te hicieron sentir
      y encontrá nuevas historias a través de los ojos de otros.
      El cine también se vive después de los créditos.
    </p>
    <button class="primary-btn" onclick="document.getElementById('peliculas').scrollIntoView({behavior:'smooth'})">
      Explorar películas →
    </button>
  </div>
</section>

<main>
  <section id="peliculas">
    <div class="section-heading">
      <div>
        <div class="eyebrow">La colección</div>
        <h2>Películas para sentir</h2>
      </div>
      <span class="muted" id="movieCount"></span>
    </div>

    <div class="controls">
      <input id="search" type="search" placeholder="Buscar una película...">
      <select id="genre">
        <option value="">Todos los géneros</option>
        <option value="Drama">Drama</option>
        <option value="Romance">Romance</option>
        <option value="Ciencia ficción">Ciencia ficción</option>
        <option value="Suspenso">Suspenso</option>
        <option value="Animación">Animación</option>
        <option value="Fantasía">Fantasía</option>
      </select>
      <select id="sort">
        <option value="default">Orden original</option>
        <option value="rating">Mejor puntuadas</option>
        <option value="title">Título A–Z</option>
      </select>
    </div>

    <div class="movie-grid" id="movieGrid"></div>
  </section>

  <section class="review-section" id="resenas">
    <div class="section-heading">
      <div>
        <div class="eyebrow">La comunidad</div>
        <h2>Tu opinión cuenta</h2>
        <p class="muted">Elegí una película, puntuála y contá qué te pareció.</p>
      </div>
    </div>

    <div class="review-layout">
      <div class="panel">
        <h3>Escribí tu reseña</h3>
        <p class="muted">Una película, cinco estrellas posibles y tu propia historia.</p>

        <form id="reviewForm">
          <label class="form-label" for="movieSelect">Película</label>
          <select id="movieSelect" class="form-input" required></select>

          <label class="form-label" for="username">Tu nombre o usuario</label>
          <input id="username" class="form-input" maxlength="35"
                 placeholder="Ej. cinefila.jpg" required>

          <label class="form-label">Tu puntuación</label>
          <div class="star-picker" id="starPicker" aria-label="Elegir puntuación"></div>
          <div class="rating-hint" id="ratingHint">Elegí entre 0,5 y 5 estrellas</div>

          <label class="form-label" for="reviewText">Tu reseña</label>
          <textarea id="reviewText" class="form-textarea" maxlength="1200"
                    placeholder="¿Qué te hizo sentir? ¿La recomendarías?" required></textarea>

          <button type="submit" class="primary-btn">Publicar reseña ✦</button>

          <p class="notice">
            Tus reseñas se guardan en este navegador. No se publican en internet
            ni son visibles para otros dispositivos.
          </p>
        </form>
      </div>

      <div class="panel">
        <h3>Lo que dice la comunidad</h3>
        <p class="muted" id="communitySubtitle">Reseñas de las películas</p>
        <div id="reviewList"></div>
      </div>
    </div>
  </section>
</main>

<footer>
  <strong>CINÉORA</strong>
  Un espacio para quienes encuentran algo de sí mismos en una película.
  <p>Hecho para amantes del cine ♡</p>
</footer>

<script>
const movies = [
  {
    id: 1, title: "Interstellar", year: 2014,
    genre: "Ciencia ficción", director: "Christopher Nolan",
    poster: "https://image.tmdb.org/t/p/w500/gEU2QniE6E77NI6lCU6MxlNBvIx.jpg",
    description: "Un viaje más allá de las estrellas que explora el tiempo, el amor y todo lo que estamos dispuestos a hacer por quienes queremos."
  },
  {
    id: 2, title: "La La Land", year: 2016,
    genre: "Romance", director: "Damien Chazelle",
    poster: "https://image.tmdb.org/t/p/w500/uDO8zWDhfWwoFdKS4fzkUJt0Rf0.jpg",
    description: "Dos personas persiguen sus sueños en Los Ángeles mientras descubren lo difícil que puede ser elegir entre el amor y aquello que desean ser."
  },
  {
    id: 3, title: "Los juegos del hambre", year: 2012,
    genre: "Acción/aventura", director: "Gary Ross",
    poster: “https://share.google/images/tytRl3nFvNLWy57Qz",
    description: "Los juegos del hambre es una novela de ciencia ficción y aventuras escrita por Suzanne Collins, ambientada en la nación distópica de Panem, construida sobre lo que alguna vez fue Norteamérica."
  },
  {
    id: 4, title: "Orgullo y prejuicio", year: 2005,
    genre: "Romance", director: "Joe Wright",
    poster: "https://image.tmdb.org/t/p/w500/sGjIvtVvTlWnia2zfJfHz81pZ9Q.jpg",
    description: "Una historia de amor, primeras impresiones y sentimientos que aparecen donde menos se esperan."
  },
  {
    id: 5, title: "El origen", year: 2010,
    genre: "Ciencia ficción", director: "Christopher Nolan",
    poster: "https://image.tmdb.org/t/p/w500/oYuLEt3zVCKq57qu2F8dT7NIa6f.jpg",
    description: "Un especialista capaz de entrar en los sueños recibe una misión que desafía los límites entre la realidad y la imaginación."
  },
  {
    id: 6, title: "Titanic", year: 1997,
    genre: "Romance", director: "James Cameron",
    poster: "https://image.tmdb.org/t/p/w500/9xjZS2rlVxm8SFx8kPC3aIGCOYQ.jpg",
    description: "Dos jóvenes de mundos diferentes se conocen durante un viaje que cambiará sus vidas para siempre."
  },
  {
    id: 7, title: "Cisne negro", year: 2010,
    genre: "Suspenso", director: "Darren Aronofsky",
    poster: "https://image.tmdb.org/t/p/w500/viWheBd44bouiLCHgNMvahLThqx.jpg",
    description: "Una bailarina se enfrenta a las exigencias de la perfección mientras la presión transforma su mundo."
  },
  {
    id: 8, title: "El castillo ambulante", year: 2004,
    genre: "Fantasía", director: "Hayao Miyazaki",
    poster: "https://image.tmdb.org/t/p/w500/6pZgH10jhpToPcf0uvyTCPFhWpI.jpg",
    description: "Una joven encuentra un castillo mágico y descubre que la aventura puede cambiar la forma en que se ve a sí misma."
  }
];

const demoReviews = [
  {
    id: "demo1", movieId: 2, user: "luna.cine",
    rating: 5, text: "La música, los colores y esa sensación de soñar con algo enorme. Una de esas películas que te dejan pensando incluso después de terminar.",
    date: "2026-10-12", helpful: 12, demo: true
  },
  {
    id: "demo2", movieId: 1, user: "framebyframe",
    rating: 4.5, text: "Visualmente increíble y con una historia que te hace pensar en el tiempo y en las personas que amamos. Me dejó con un montón de emociones.",
    date: "2026-10-08", helpful: 8, demo: true
  },
  {
    id: "demo3", movieId: 4, user: "mieldepelicula",
    rating: 5, text: "La tensión de las miradas y todo lo que no se dicen. Es preciosa y tiene una atmósfera que me encanta.",
    date: "2026-10-03", helpful: 5, demo: true
  }
];

function readStorage(key, fallback) {
  try {
    const value = localStorage.getItem(key);
    return value ? JSON.parse(value) : fallback;
  } catch (e) {
    return fallback;
  }
}

let reviews = readStorage("cineora_reviews", demoReviews);
let favorites = readStorage("cineora_favorites", []);
let selectedRating = 0;
let favoritesOnly = false;

const $ = id => document.getElementById(id);

function saveData() {
  try {
    localStorage.setItem("cineora_reviews", JSON.stringify(reviews));
    localStorage.setItem("cineora_favorites", JSON.stringify(favorites));
  } catch (e) {
    console.warn("No se pudieron guardar los datos en este navegador.");
  }
}

function averageRating(movieId) {
  const list = reviews.filter(r => Number(r.movieId) === Number(movieId));
  if (!list.length) return null;
  return list.reduce((sum, r) => sum + Number(r.rating), 0) / list.length;
}

function reviewCount(movieId) {
  return reviews.filter(r => Number(r.movieId) === Number(movieId)).length;
}

function escapeHTML(value) {
  return String(value).replace(/[&<>"']/g, char => ({
    "&": "&amp;", "<": "&lt;", ">": "&gt;",
    '"': "&quot;", "'": "&#039;"
  })[char]);
}

function renderMovies() {
  const query = $("search").value.toLowerCase().trim();
  const genre = $("genre").value;
  const sort = $("sort").value;

  let list = movies.filter(movie => {
    const matchesQuery = (movie.title + " " + movie.director + " " + movie.genre)
      .toLowerCase().includes(query);
    const matchesGenre = !genre || movie.genre === genre;
    const matchesFavorite = !favoritesOnly || favorites.includes(movie.id);
    return matchesQuery && matchesGenre && matchesFavorite;
  });

  if (sort === "title") {
    list.sort((a, b) => a.title.localeCompare(b.title));
  } else if (sort === "rating") {
    list.sort((a, b) => (averageRating(b.id) || 0) - (averageRating(a.id) || 0));
  }

  $("movieCount").textContent = list.length + (list.length === 1 ? " película" : " películas");

  $("movieGrid").innerHTML = list.map(movie => {
    const avg = averageRating(movie.id);
    const isFavorite = favorites.includes(movie.id);

    return `
      <article class="movie-card">
        <div class="poster" onclick="selectMovie(${movie.id})">
          <div class="poster-fallback">${escapeHTML(movie.title)}</div>
          <img src="${movie.poster}" alt="Póster de ${escapeHTML(movie.title)}"
               loading="lazy"
               onload="this.previousElementSibling.style.display='none'"
               onerror="this.style.display='none'">
          <button class="favorite ${isFavorite ? "active" : ""}"
                  aria-label="Agregar a favoritos"
                  onclick="toggleFavorite(event, ${movie.id})">
            ${isFavorite ? "♥️" : "♡"}
          </button>
          <div class="poster-label">${escapeHTML(movie.genre)}</div>
        </div>
        <div class="movie-title">${escapeHTML(movie.title)}</div>
        <div class="movie-meta">${movie.year} · ${escapeHTML(movie.director)}</div>
        <div class="rating-line">
          ${avg !== null ? "★ " + avg.toFixed(1) : "☆ Sin puntuar"}
          <span> · ${reviewCount(movie.id)} reseña(s)</span>
        </div>
        <button class="secondary-btn" onclick="selectMovie(${movie.id})">
          Ver reseñas
        </button>
      </article>`;
  }).join("") || '<p class="empty">No encontramos películas con esos filtros.</p>';
}

function toggleFavorite(event, id) {
  event.stopPropagation();
  if (favorites.includes(id)) {
    favorites = favorites.filter(f => f !== id);
  } else {
    favorites.push(id);
  }
  saveData();
  renderMovies();
}

function selectMovie(id) {
  $("movieSelect").value = String(id);
  $("communitySubtitle").textContent = "Reseñas de " + movies.find(m => m.id === id).title;
  renderReviews(id);
  $("resenas").scrollIntoView({ behavior: "smooth" });
}

function renderMovieOptions() {
  $("movieSelect").innerHTML = movies.map(movie =>
    `<option value="${movie.id}">${escapeHTML(movie.title)}</option>`
  ).join("");
}

function drawStars() {
  const picker = $("starPicker");
  picker.innerHTML = "";

  for (let i = 1; i <= 5; i++) {
    const star = document.createElement("span");
    star.className = "star" + (selectedRating >= i ? " selected" : "");
    star.textContent = "★";
    star.title = i + " estrella(s)";
    star.setAttribute("role", "button");
    star.setAttribute("tabindex", "0");
    star.setAttribute("aria-label", i + " estrellas");

    // Click en la mitad izquierda = media estrella.
    // Click en la mitad derecha = estrella completa.
    function chooseStar(event) {
      const rect = star.getBoundingClientRect();
      const half = event.clientX - rect.left < rect.width / 2;
      selectedRating = half ? i - 0.5 : i;
      $("ratingHint").textContent = "Tu puntuación: " + selectedRating.toFixed(1) + " / 5";
      drawStars();
    }

    star.addEventListener("click", chooseStar);
    star.addEventListener("keydown", event => {
      if (event.key === "Enter" || event.key === " ") {
        event.preventDefault();
        selectedRating = i;
        $("ratingHint").textContent = "Tu puntuación: " + selectedRating.toFixed(1) + " / 5";
        drawStars();
      }
    });

    picker.appendChild(star);
  }

  [...picker.children].forEach((star, index) => {
    if (selectedRating >= index + 1) {
      star.classList.add("selected");
    } else if (selectedRating === index + 0.5) {
      star.classList.add("selected");
      star.style.background = "linear-gradient(90deg, var(--pink2) 50%, #594653 50%)";
      star.style.color = "transparent";
      star.style.backgroundClip = "text";
    }
  });
}

function formatDate(date) {
  return new Date(date + "T12:00:00").toLocaleDateString("es-AR", {
    day: "numeric", month: "short", year: "numeric"
  });
}

function renderReviews(movieId = null) {
  const list = reviews
    .filter(r => movieId === null || Number(r.movieId) === Number(movieId))
    .slice()
    .sort((a, b) => b.date.localeCompare(a.date));

  $("reviewList").innerHTML = list.map(review => `
    <article class="review-card">
      <div class="review-top">
        <div>
          <div class="review-name">${escapeHTML(review.user)}
            ${review.demo ? '<span class="muted">(ejemplo)</span>' : ""}
          </div>
          <div class="review-date">${formatDate(review.date)}</div>
        </div>
        <div class="review-stars" aria-label="${review.rating} de 5">
          ${"★".repeat(Math.floor(review.rating))}${review.rating % 1 ? "½" : ""}
        </div>
      </div>
      <div class="review-text">${escapeHTML(review.text)}</div>
      <div class="muted">${escapeHTML(movies.find(m => m.id === Number(review.movieId))?.title || "")}</div>
      <button class="helpful" onclick="voteHelpful('${review.id}')">
        ♡ Útil (${review.helpful || 0})
      </button>
    </article>
  `).join("") || '<div class="empty">Todavía no hay reseñas para esta película. ¡Sé la primera persona en escribir una!</div>';
}

function voteHelpful(id) {
  const review = reviews.find(r => String(r.id) === String(id));
  if (!review) return;
  review.helpful = (review.helpful || 0) + 1;
  saveData();
  renderReviews($("movieSelect").value || null);
}

$("reviewForm").addEventListener("submit", event => {
  event.preventDefault();

  const user = $("username").value.trim();
  const text = $("reviewText").value.trim();
  const movieId = Number($("movieSelect").value);

  if (!user || !text || !movieId || selectedRating < 0.5) {
    alert("Completá tu nombre, la reseña y elegí una puntuación.");
    return;
  }

  reviews.push({
    id: "review_" + Date.now(),
    movieId,
    user,
    rating: selectedRating,
    text,
    date: new Date().toISOString().slice(0, 10),
    helpful: 0,
    demo: false
  });

  saveData();
  event.target.reset();
  selectedRating = 0;
  $("ratingHint").textContent = "Elegí entre 0,5 y 5 estrellas";
  drawStars();
  renderMovies();
  renderReviews(movieId);
  $("communitySubtitle").textContent = "Reseñas de " + movies.find(m => m.id === movieId).title;
  alert("¡Tu reseña quedó guardada en este navegador! ♡");
});

$("search").addEventListener("input", renderMovies);
$("genre").addEventListener("change", renderMovies);
$("sort").addEventListener("change", renderMovies);

$("movieSelect").addEventListener("change", () => {
  const id = Number($("movieSelect").value);
  const movie = movies.find(m => m.id === id);
  $("communitySubtitle").textContent = "Reseñas de " + movie.title;
  renderReviews(id);
});

$("favoritesLink").addEventListener("click", event => {
  event.preventDefault();
  favoritesOnly = !favoritesOnly;
  $("favoritesLink").textContent = favoritesOnly ? "♡ Ver todas" : "♡ Favoritas";
  $("peliculas").scrollIntoView({ behavior: "smooth" });
  renderMovies();
});

renderMovieOptions();
drawStars();
renderMovies();
renderReviews();
</script>

</body>
</html>
